---
description: Performing sequential tasks with Pipelines in Vendr, the eCommerce solution for Umbraco
---

# Pipelines

Pipelines allow a series of tasks to be performed in a set sequence. This is done with the input of a given task being the output of the preceding task. It allows a result to be built up as an input is passed through these individual tasks, instead of being calculated in one go.

The Pipelines feature provides an approach to insert additional steps into the process as pipeline tasks can be added or removed from the pipeline sequence.

Where Pipelines is used, it allows an additional point at which developers can interject some custom logic, tweaking how Vendr works.

Consider these use-case examples:

* An additional task could be injected into the `CalculateOrderPipeline` to alter how an Order is calculated.
* A task could be injected into the `EmailSendPipeline` to add a dynamic attachment to an email.

## Example Pipeline task

An example of a Pipeline task would look something like this:

```csharp
public class AddCustomAttachmentTask : PipelineTaskWithTypedArgsBase<EmailSendPipelineArgs, EmailContext>
{
    public override PipelineResult<EmailContext> Execute(EmailSendPipelineArgs args)
    {
        var attachment = new Attachment(File.OpenRead("path\to\license.lic"), "license.lic");

        args.EmailContext.MailMessage.Attachments.Add(attachment);

        return Ok(args.EmailContext);
    }
}
```

All Pipeline tasks inherit from a base class `PipelineTaskWithTypedArgsBase<TPipelineArgs, TModel>`. `TPipelineArgs` is the Type of the arguments supported by the pipeline and `TModel` is the pipelines return model Type. You then need to implement an `Execute` method which accepts an instance of the arguments type as input and expects a `PipelineResult<TModel>` as it's output. Inside this method you can perform your custom logic as required. To complete the pipeline task, you can call `Ok(TModel)` if the task was successful. This will pass in the updated `TModel` instance to returnæ. Otherwise you can call `Fail()` to fail the whole pipeline.

All pipelines occur within a [Unit of Work](../unit-of-work/). In case a Pipeline task fails, the whole pipeline will fail and no changes will the persisted.

## Registering a Pipeline task

Pipeline tasks are [registered via the IVendrBuilder](../vendr-builder/#registering-dependencies) interface using the appropriate `With{PipelineName}Pipeline()` builder extension method. This is done to identify the pipeline you want to extend. You can then call the `Append<TTask>()` method to append your task onto the end of that pipeline.

```csharp
public static class VendrBuilderExtensions
{
    public static IVendrBuilder AddMyPipelineTasks(IVendrBuilder builder)
    {
        // Add our custom pipeline tasks
        builder.WithSendEmailPipeline()
            .Append<LogEmailSentTask>();

        // Return the builder to continue the chain
        return builder;
    }
}
```

You can also control the order of when Pipeline tasks run, before or after another task, by appending them via the `InsertBefore<TTask>()` or `InsertAfter<TTask>()` methods respectively.

```csharp
public static class VendrBuilderExtensions
{
    public static IVendrBuilder AddMyPipelineTasks(IVendrBuilder builder)
    {
        // Register AddCustomAttachmentTask to execute before the SendSmtpEmail handler
        builder.WithSendEmailPipeline()
            .InsertBefore<SendSmtpEmail, AddCustomAttachmentTask>();

        // Register LogEmailSentTask to execute after the SendSmtpEmail handler
        builder.WithSendEmailPipeline()
            .InsertAfter<SendSmtpEmail, LogEmailSentTask>();

        // Return the builder to continue the chain
        return builder;
    }
}
```