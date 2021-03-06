# AWS CodePipeline Permissions Reference<a name="permissions-reference"></a>

When you are setting up [Access Control with IAM Policies](access-control.md) and writing permissions policies that you can attach to an IAM identity \(identity\-based policies\), you can use the following table as a reference\. The table lists each AWS CodePipeline API operation and the corresponding actions for which you can grant permissions to perform the action\. You specify the actions in the policy's `Action` field, and you specify a wildcard character \(\*\) as the resource value in the policy's `Resource` field\.

You can use AWS\-wide condition keys in your AWS CodePipeline policies to express conditions\. For a complete list of AWS\-wide keys, see [Available Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html#AvailableKeys) in the *IAM User Guide*\.

**Note**  
To specify an action, use the `codepipeline:` prefix followed by the API operation name\. For example: `codepipeline:GetPipeline`, `codepipeline:CreatePipeline`, or `codepipeline:*` \(for all AWS CodePipeline actions\)\.

To specify multiple actions in a single statement, separate them with commas as follows:

```
"Action": ["codepipeline:action1", "codepipeline:action2"]
```

You can also specify multiple actions using wildcards\. For example, you can specify all actions whose name begins with the word "Get" as follows:

```
"Action": "codepipeline:Get*"
```

To specify all AWS CodePipeline API actions, use the \* wildcard as follows:

```
"Action": "codepipeline:*"
```

The actions you can specify in an IAM policy for use with AWS CodePipeline are listed below\.


**AWS CodePipeline API Operations and Required Permissions for Actions**  

| AWS CodePipeline API Operations | Required Permissions \(API Actions\) | 
| --- | --- | 
|  [AcknowledgeJob](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_AcknowledgeJob.html)  |  `codepipeline:AcknowledgeJob` Required to view information about a specified job and whether that job has been received by the job worker\. Only used for custom actions\.  | 
|  [AcknowledgeThirdPartyJob](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_AcknowledgeThirdPartyJob.html)  |  `codepipeline:AcknowledgeThirdPartyJob` Required to confirm a job worker has received the specified job\. Only used for partner actions\.  | 
|  [CreateCustomActionType](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_CreateCustomActionType.html)  |  `codepipeline:CreateCustomActionType` Required to create a new custom action that can be used in all pipelines associated with the AWS account\. Only used for custom actions\.  | 
|  [CreatePipeline](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_CreatePipeline.html)  |  `codepipeline:CreatePipeline` Required to create a pipeline\.  | 
|  [DeleteCustomActionType](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_DeleteCustomActionType.html)  |  `codepipeline:DeleteCustomActionType` Required to mark a custom action as deleted\. PollForJobs for the custom action will fail after the action is marked for deletion\. Only used for custom actions\.  | 
|  [DeletePipeline](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_DeletePipeline.html)  |  `codepipeline:DeletePipeline` Required to delete a pipeline\.  | 
|  [DisableStageTransition](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_DisableStageTransition.html)  |  `codepipeline:DisableStageTransition` Required to prevent artifacts in a pipeline from transitioning to the next stage in the pipeline\.  | 
|  [EnableStageTransition](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_EnableStageTransition.html)  |  `codepipeline:EnableStageTransition` Required to enable artifacts in a pipeline to transition to a stage in a pipeline\.  | 
|  [GetJobDetails](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_GetJobDetails.html)  |  `codepipeline:GetJobDetails` Required to retrieve information about a job\. Only used for custom actions\.  | 
|  [GetPipeline](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_GetPipeline.html)  |  `codepipeline:GetPipeline` Required to retrieve the structure, stages, actions, and metadata of a pipeline, including the pipeline ARN\.  | 
|  [GetPipelineExecution](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_GetPipelineExecution.html)  |  `codepipeline:GetPipelineExecution` Required to retrieve information about an execution of a pipeline, including details about artifacts, the pipeline execution ID, and the name, version, and status of the pipeline\.  | 
|  [GetPipelineState](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_GetPipelineState.html)  |  `codepipeline:GetPipelineState` Required to retrieve information about the state of a pipeline, including the stages and actions\.  | 
|  [GetThirdPartyJobDetails](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_GetThirdPartyJobDetails.html)  |  `codepipeline:GetThirdPartyJobDetails` Required to request the details of a job for a third party action\. Only used for partner actions\.  | 
|  [ListActionTypes](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_ListActionTypes.html)  |  `codepipeline:ListActionTypes` Required to generate a summary of all AWS CodePipeline action types associated with your account\.  | 
|  [ListPipelineExecutions](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_ListPipelineExecutions.html)  |  `codepipeline:ListPipelineExecutions` Required to generate a summary of the most recent executions for a pipeline\.  | 
|  [ListPipelines](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_ListPipelines.html)  |  `codepipeline:ListPipelines` Required to generate a summary of all of the pipelines associated with your account\.  | 
|  [PollForJobs](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_PollForJobs.html)  |  `codepipeline:PollForJobs` Required to retrieve information about any jobs for AWS CodePipeline to act upon\.  | 
|  [PollForThirdPartyJobs](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_PollForThirdPartyJobs.html)  |  `codepipeline:PollForThirdPartyJobs` Required to determine whether there are any third party jobs for a job worker to act on\. Only used for partner actions\.  | 
|  [PutActionRevision](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_PutActionRevision.html)  |  `codepipeline:PutActionRevision` Required to report information to AWS CodePipeline about new revisions to a source  | 
|  [PutApprovalResult](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_PutApprovalResult.html)  |  `codepipeline:PutApprovalResult` Required to report the response to a manual approval request to AWS CodePipeline\. Valid responses include Approved and Rejected\.  | 
|  [PutJobFailureResult](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_PutJobFailureResult.html)  |  `codepipeline:PutJobFailureResult` Required to report the failure of a job as returned to the pipeline by a job worker\. Only used for custom actions\.  | 
|  [PutJobSuccessResult](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_PutJobSuccessResult.html)  |  `codepipeline:PutJobSuccessResult` Required to report the success of a job as returned to the pipeline by a job worker\. Only used for custom actions\.  | 
|  [PutThirdPartyJobFailureResult](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_PutThirdPartyJobFailureResult.html)  |  `codepipeline:PutThirdPartyJobFailureResult` Required to report the failure of a third party job as returned to the pipeline by a job worker\. Only used for partner actions\.  | 
|  [PutThirdPartyJobSuccessResult](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_PutThirdPartyJobSuccessResult.html)  |  `codepipeline:PutThirdPartyJobSuccessResult` Required to report the success of a third party job as returned to the pipeline by a job worker\. Only used for partner actions\.   | 
|  [RetryStageExecution](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_RetryStageExecution.html)  |  `codepipeline:RetryStageExecution` Required to resume the pipeline execution by retrying the last failed actions in a stage\.  | 
|  [StartPipelineExecution](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_StartPipelineExecution.html)  |  `codepipeline:StartPipelineExecution` Required to start the specified pipeline\. Specifically, it begins processing the latest commit to the source location specified as part of the pipeline\.  | 
|  [UpdatePipeline](http://docs.aws.amazon.com/codepipeline/latest/APIReference/API_UpdatePipeline.html)  |  `codepipeline:UpdatePipeline` Required to update a specified pipeline with edits or changes to its structure\.  | 