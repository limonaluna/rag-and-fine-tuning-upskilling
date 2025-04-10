# LLM Fine-Tuning using Azure 
A fine-tuning guide for both OpenAI and Open-Source Large Lauguage Models on Azure. This repo. is designed to be user-friendly for people with non-technical background and for people with technical background such as Data Scientists and Machine Learning Engineers.

## What
Fine-Tuning, or *Supervised Fine-Tuning*, retrains an existing pre-trained LLM using example data, resulting in a new "custom" fine-tuned LLM that has been optimized for the provided task-specific examples. 
![What is Fine-Tuning](./../media/07-fine-tuned-llm.png)

## Why
Typically, we use Fine-Tuning to:
- improve LLM performance on specific tasks.
- introduce information that wasn't well represented by the base LLM model.

Good use cases include: 
- steering the LLM outputs in a specific style or tone.
- too long or complex prompts to fit into the LLM prompt window.

## When
You may consider Fine-Tuning when:
- you have tried Prompt Engineering and RAG approaches.
- latency is critically important to the use case.
- high accuracy is required to meet the customer requirement.
- you have thousands of high-quality samples with ground-truth data.
- you have clear evaluation metrics to benchmark fine-tuned models.


# Hands-On Lab
## Fine-Tuning GPT Models - A Dashboard Experience
Learn how to fine-tune a GPT model using Azure OpenAI Studio - UI Dashboard.  

### Prerequisites
* Learn the [what, why, and when to use fine-tuning.](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/fine-tuning-considerations)
* An Azure subscription.
* Access to Azure OpenAI Service.
* An Azure OpenAI resource created in the supported fine-tuning region (e.g. Sweden Central).
* GPT Models that support fine-tuning so far: *gpt-35-turbo-0613* and *gpt-35-turbo-1106*.
* Prepare Training and Validation datasets:
  * at least 50 high-quality samples (preferably 1,000s) are required.
  * must be formatted in the JSON Lines (JSONL) document with UTF-8 encoding.

You can check the MS Learn document [here](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/fine-tuning?tabs=turbo%2Cpython&pivots=programming-language-studio) for more details.

### Step 1: Open the *Create a custom model* wizard
1. Open Azure OpenAI Studio at [https://oai.azure.com/](https://oai.azure.com/) and sign in with credentials that have access to your Azure OpenAI resource. During the sign-in workflow, select the appropriate directory, Azure subscription, and Azure OpenAI resource.
2. In Azure Foundry, browse to the **Tools > Fine-Tuning** pane, and select **Fine-tune model**.
![Fine-tune base model](./../media/07-fine-tune-wizard.png)

### Step 2: Select the *Base model*
The first step in creating a custom model is to choose a base model. 

The **Base model** pane lets you choose a base model to use for your custom model. Select the base model from the **Base model type** dropdown, and then select **Next** to continue.
![Base Model selection](./../media/07-base-model-selection.png)

### Step 3: Configure your *Fine-Tuning Method*
First, you need to choose the Fine-Tuning Method. We choose **Supervised** Method for this tutorial.
![Fine-Tuning Method](./../media/07-fine-tune-wizard2.png)


### Step 4: Upload your *Training Data*
The next step is to choose your training data either from the previously uploaded one or by uploading a new one. If you want to create your own training data, please note the following guidance on the required format of the training and validation data: [Guidance on data format](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/fine-tuning?tabs=azure-openai&pivots=programming-language-studio#prepare-your-training-and-validation-data)

Select **Local file** to upload training data from a local file - the sample training data can be found in this repository under "07-LLM-Fine-Tuning/data/training_set.jsonl"

![Upload training data](./../media/07-upload-training-data.png)

### Step 5: Upload your *Validation Data*
You can choose your validation data by following the similar pattern as you upload your training data.

### Step 6 (Optional): Configure *Advanced options*
You can keep the **Default** values for the fine-tuning job, or adjust the **Hyperparameters** as desired.

One can refer to the MS Learn document [here](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/fine-tuning?tabs=turbo%2Cpython&pivots=programming-language-studio#configure-advanced-options) for a detailed explanation on key tun-able hyperparameters.

### Step 7: Review your choices, *Submit Training job* and check the *Status*
If you're ready to train your model, select **Submit** to start the fine-tuning job and return to the **Fine-Tuning** pane.

You can check the status of the fine-tuned model in the **Status** column of the **Fine-Tuning** tab.
![Status of Fine-Tuning](./../media/07-fine-tuning-status.png)

After you start a fine-tuning job, it can take some time to complete (from minutes to hours). You can also dive deeper by reviewing the **Details**, **Logs**, and **Checkpoints** Tab after clicking on your fine-tune model training run.

* Fine Tuning Run Details:
![Fine Tune Training Run Details](./../media/07-fine-tune-training-details.png)

* Fine Tuning Run Logs:
![Fine Tune Training Logs](./../media/07-fine-tune-training-logs.png)






### Step 8: Deploy a custom model
When the fine-tuning job succeeds, you can deploy the custom model from the **Models** pane to make it available for use with completion calls.

To deploy your custom model, select the custom model to deploy, and then select **Deploy model**.
<ol><img src="https://learn.microsoft.com/en-us/azure/ai-services/openai/media/fine-tuning/studio-models-deploy-model.png#lightbox
" alt="Screenshot that shows how to deploy a custom model in Azure OpenAI Studio." width="600"/></ol>

The **Deploy model** dialog box opens. 

In the dialog box, enter your **Deployment name** and then select **Create** to start the deployment of your custom model.
<ol><img src="https://learn.microsoft.com/en-us/azure/ai-services/openai/media/fine-tuning/studio-models-deploy.png" alt="Screenshot of the Deploy Model dialog in Azure OpenAI Studio." width="600"/></ol>

### Step 8: Test and use a deployed model
After your custom model deploys, you can use it like any other deployed model. 

You can use the **Playgrounds** in [Azure OpenAI Studio]("https://oai.azure.com") to experiment with your new deployment. You can also use the fine-tuned model by calling the completion API.

### Step 9 (Optional): Clean up your deployment resources
When you're done with your custom model, you can delete the deployment and model. You can also delete the training and validation files you uploaded to the service, if needed.

### Step 10 (Optional): Continous fine-tuning
Once you have created a fine-tuned model you may wish to continue to refine the model over time through further fine-tuning. Continuous fine-tuning is the iterative process of selecting an already fine-tuned model as a base model and fine-tuning it further on new sets of training examples.

To perform fine-tuning on a model that you have previously fine-tuned you would use the same process as described in **Step 1**, but instead of specifying the name of a generic base model, you would specify your already fine-tuned model. A custom fine-tuned model would look like <code>gpt-35-turbo-0613.ft-5fd1918ee65d4cd38a5dcf6835066ed7</code>
<ol><img src="https://learn.microsoft.com/en-us/azure/ai-services/openai/media/fine-tuning/studio-continuous.png" alt="Screenshot of the Create a custom model UI with a fine-tuned model highlighted." width="600"/></ol>

