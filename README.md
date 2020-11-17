# VoiceMate

## What is it?

VoiceMate is an application that converts voice into sign language using AWS services.

The system was developed using these AWS services & technologies:

- Amazon Sumerian
- Amazon Transcribe
- Amazon Polly
- Amazon Cognito
- Amazon CloudFormation
- Amazon Lambda

## This is what you will have by the end of this tutorial

![Image description](./Images/Voicemate.png)

## How to create the scene ?

First, you need to [log into you AWS account](https://aws.amazon.com/console/) or if you don’t have one you can easily [create a new AWS account](https://aws.amazon.com/resources/create-account/).

![Image description](./Images/Log_in.png)

Once you are logged in, go to services and search for Amazon Sumerian.

![Image description](./Images/Sumerina_Editor.png)

When the Sumerian console loads, click on **Create new scene**.

![Image description](./Images/Create_name.png)

Enter a name for your scene then hit enter. It will take you to the Sumerian Editor.

![Image description](./Images/Import_asset.png)

In the editor, click on **Import asset** and upload the [provided sumerian bundle file](https://github.com/bahrain-uob/VoiceMate/blob/master/src/VoiceMate_v1.1_Bundle.zip).

![Image description](./Images/Upload_bundle.png)

After you import the bundle, you need to add a Cognito Id that grants the sumerian scene access to AWS Resources.

To do that, first we will create an [AWS CloudFormation stack](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/quickcreate?templateURL=https:%2F%2Fs3.amazonaws.com%2Fsumerian-cfn-templates%2FTranscribeStreamingLexPollyExampleTemplate.yml&stackName=AmazonSumerianTrascribeStreamingStack)

This stack is an AWS CloudFormation template that will spin up the required resources to get you up and running quickly. The AWS CloudFormation template will do the following:

- Create an Amazon Cognito identity pool with IAM (Identity and Access Management) policies for Amazon Lex, Amazon Polly, and Amazon Transcribe streaming transcription.

- Output the Cognito identity pool ID

![Image description](./Images/Create_cognito.png)

Copy the Cognito Id that you generated and paste it into the Sumerian scene.

![Image description](./Images/Copy_Cognito.png) 
 
Add the Cognito id in your scene...

![Image description](./Images/Add_cognito.png)

Now, we need to setup our Lambda function. The Lambda function will pre-process the transcribed text. Download the [provided Lambda function](https://github.com/bahrain-uob/VoiceMate/blob/master/src/sumerian-text-process-function.zip).

Go to the **AWS Lambda** console.

![Image description](./Images/Lambda_console.png)

Click on **Create function**. 

![Image description](./Images/Create_function.png)

Keep the default settings and give a name to your function.

![Image description](./Images/Function_name.png)

Then click on **Create function**.

In the function code section, expand the Code entry type drop-down list, and then choose **Upload a .zip** file.

![Image description](./Images/Upload_zip.png)

After you have uploaded the zip file successfully, copy the **ARN number**.

![Image description](./Images/Copy_Arn.png)

Go back to the Sumerian editor. First in the **Entities** panel, click on the entity named "Habib" and then in the **Script** panel, click on the edit scipt icon (pencil icon).

![Image description](./Images/Edit_code.png)

It will open a new window. In the **AnimationScript** replace the highlighted code with the **ARN number** that you copied in the previous step while creating the Lambda function.

![Image description](./Images/Change_code.png)

After you have changed it. Save and close the text editor.

# The Scene

Once you’re done with setting up the CloudFormation stack, importing the bundle, creating a lambda function and setting up the Cognito ID. You will be presented with the following scene.

![Image description](./Images/Scene.png)

There are two main entities in this scene:

-	The HTML entity labeled “AudioTranscription”
-	The 3D character model

### AudioTranscription

The scripts on this component handle the realtime audio transcription to text. This feature was added from the following Amazon Sumerian article: [Hands-Free Chatbot and Voice Transcription Using Amazon Sumerian](https://docs.sumerian.amazonaws.com/articles/hands-free-voice-transcription/).
  
### Character Pack

The 3d model in the scene has an **Animation** component attached which has all the states linked to their respective animation clips. The model was purchased and animations were created in [Blender3D](https://www.blender.org/), a popular 3D modelling software. Any other software can be used as well.

The 3d model also has a **Script** component attached. The “AnimationScript” handles all the logic to play animations based on the transcribed text.


# How to use it?

Click on the play button to start the scene.
![Image description](./Images/Play.png)

Then click on the **Start** button.

For demo purposes, try the following paragraph on COVID-19:

>Coronavirus disease is an infectious disease caused by a newly discovered coronavirus.
>
>Most people infected with the corona virus will experience mild to moderate respiratory illness and recover without requiring special treatment.
>
>The best way to prevent and slow down transmission is be well informed about the corona virus, the disease it causes and how it spreads.
>
>Protect yourself and others from infection by washing your hands or using an alcohol based rub frequently and not touching your face.
>
>At this time, there are no specific treatments for corona virus. However, there are many ongoing clinical trials evaluating potential treatments.


You can test it out by reading the paragraph.

The scene will take the audio input and then convert into the sign language.


You can also make changes to the scene according to your own needs. Once you are done modifying the scene, then you have to publish it, choose **Publish** in the upper-right corner, and then choose **Create public link**.

![Image description](./Images/Create_link.png)
![Image description](./Images/Publish.png)

![Image description](./Images/link.png)

With the link that is generated, you can view and interact with the scene on the web across any supported browser/device.

## Pricing


As part of the AWS Free Tier, you can get started with Amazon Sumerian for free. Upon sign-up, new customers can create up to a 50MB published scene that receives the equivalence of 100 views (5GB) per month, for the first 12 months.

You are charged for the total size of the 3D assets you upload and store in Sumerian at the rate of $0.06 per GB per month.

For more info check out [Amazon Sumerian Pricing](https://aws.amazon.com/sumerian/pricing/).

## References

The feature of Amazon Transcribing Service was added following this article on [Hands-Free Chatbot and Voice Transcription Using Amazon Sumerian](https://docs.sumerian.amazonaws.com/articles/hands-free-voice-transcription/).

The 3D model was purchased from [here](https://www.turbosquid.com/3d-models/arab-man-rigged-max/1037750).
