# Working with Stage Transitions in AWS CodePipeline<a name="transitions"></a>

Transitions are links between pipeline stages that can be disabled or enabled\. They are enabled by default\. When you re\-enable a disabled transition, the latest revision will run through the remaining stages of the pipeline unless more than 30 days have passed\. Pipeline execution won't resume for a transition that has been disabled more than 30 days unless a new change is detected or you manually rerun the pipeline\.

**Note**  
You can use an approval action to pause the run of a pipeline until it is manually approved to continue\. For more information, see [Manage Approval Actions in AWS CodePipeline](approvals.md)\. 


+ [Disable or Enable Transitions \(Console\)](#transitions-disable-enable-console)
+ [Disable or Enable Transitions \(CLI\)](#transitions-disable-enable-cli)

## Disable or Enable Transitions \(Console\)<a name="transitions-disable-enable-console"></a>

**To disable or enable transitions in a pipeline**

1. Sign in to the AWS Management Console and open the AWS CodePipeline console at [http://console\.aws\.amazon\.com/codepipeline](http://console.aws.amazon.com/codepipeline)\.

   The names of all pipelines associated with your AWS account are displayed\.

1.  In **Name**, choose the name of the pipeline for which you want to enable or disable transitions\. This opens a detailed view of the pipeline, including the transitions between the stages of the pipeline\.

1. Find the arrow after the last stage that you want to run, and then choose it\. For example, in the following example pipeline, if you want the actions in the *Staging* stage to run, but not the actions in the stage named *Production*, you would choose the arrow between those two stages:  
![\[Select the arrow between stages to enable or disable
                            transitions.\]](http://docs.aws.amazon.com/codepipeline/latest/userguide/images/codepipeline-firstpipeline.png)![\[Select the arrow between stages to enable or disable
                            transitions.\]](http://docs.aws.amazon.com/codepipeline/latest/userguide/)![\[Select the arrow between stages to enable or disable
                            transitions.\]](http://docs.aws.amazon.com/codepipeline/latest/userguide/)

1. In the **Disable transition** dialog box, type a reason for disabling the transition, and then choose **Disable**\.

   The arrow changes to show that transitions are disabled between the stage preceding the arrow and the stage following the arrow\. Any revisions that were already running in the stages that come after the disabled transition will continue through the pipeline, but any subsequent revisions will not continue past the disabled transition\.   
![\[The arrow between stages in a pipeline indicates whether a
                            transition is enabled or disabled.\]](http://docs.aws.amazon.com/codepipeline/latest/userguide/images/codepipeline-disabled-transition3.png)![\[The arrow between stages in a pipeline indicates whether a
                            transition is enabled or disabled.\]](http://docs.aws.amazon.com/codepipeline/latest/userguide/)![\[The arrow between stages in a pipeline indicates whether a
                            transition is enabled or disabled.\]](http://docs.aws.amazon.com/codepipeline/latest/userguide/)

1. To enable transitions, choose the disabled transition arrow\. In the **Enable transition** dialog box, choose **Enable**\. The pipeline will immediately enable the transition between the two stages\. If any revisions have been run through the prior stages after the transition was disabled, in a few moments, the pipeline will start running the latest revision through the stages after the formerly disabled transition\. The pipeline will run the revision through all remaining stages in the pipeline\.
**Note**  
It might take a few seconds for changes to appear in the AWS CodePipeline console after you enable the transition\.

## Disable or Enable Transitions \(CLI\)<a name="transitions-disable-enable-cli"></a>

To disable a transition between stages by using the AWS CLI, run the disable\-stage\-transition command\. To enable a disabled transition, run the enable\-stage\-transition command\. 

**To disable a transition**

1. Open a terminal \(Linux, macOS, or Unix\) or command prompt \(Windows\) and use the AWS CLI to run the [disable\-stage\-transition](http://docs.aws.amazon.com/cli/latest/reference/codepipeline/disable-stage-transition.html) command, specifying the name of the pipeline, the name of the stage to which you want to disable transitions, the transition type, and the reason you are disabling transitions to that stage\. Unlike using the console, you must also specify whether you are disabling transitions into the stage \(inbound\) or transitions out of the stage after all actions complete \(outbound\)\. 

   For example, to disable the transition to a stage named *Staging* in a pipeline named *MyFirstPipeline*, you would type a command similar to the following:

   ```
   aws codepipeline disable-stage-transition --pipeline-name MyFirstPipeline --stage-name Staging --transition-type Inbound --reason "My Reason"
   ```

   The command returns nothing\.

1. To verify the transition has been disabled, either view the pipeline in the AWS CodePipeline console or run the get\-pipeline\-state command\. For more information, see [View Pipeline Details and History \(Console\)](pipelines-view.md#pipelines-view-console) and [View Pipeline Details and History \(CLI\)](pipelines-view.md#pipelines-view-cli)\.

**To enable a transition**

1. Open a terminal \(Linux, macOS, or Unix\) or command prompt \(Windows\) and use the AWS CLI to run the [enable\-stage\-transition](http://docs.aws.amazon.com/cli/latest/reference/codepipeline/enable-stage-transition.html) command, specifying the name of the pipeline, the name of the stage to which you want to enable transitions, and the transition type\.

   For example, to enable the transition to a stage named *Staging* in a pipeline named *MyFirstPipeline*, you would type a command similar to the following:

   ```
   aws codepipeline enable-stage-transition --pipeline-name MyFirstPipeline --stage-name Staging  --transition-type Inbound
   ```

   The command returns nothing\.

1. To verify the transition has been disabled, either view the pipeline in the AWS CodePipeline console or run the get\-pipeline\-state command\. For more information, see [View Pipeline Details and History \(Console\)](pipelines-view.md#pipelines-view-console) and [View Pipeline Details and History \(CLI\)](pipelines-view.md#pipelines-view-cli)\.