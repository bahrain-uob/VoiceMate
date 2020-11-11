# VoiceMate

## What is it?

VoiceMate is an application that converts voice into sign language using Aws services.

The Voice to sign part was done using these aws services & technologies

- Amazon Sumerian
- Amazon Transcribe
- Amazon Polly
- Amazon Cognito
- Aws CloudFormation
- Aws Lambda

## This is what you will have by the end of this tutorial

![Image description](./Images/Screen%20Shot%202020-11-11%20at%208.49.03%20AM.png)

First you need to log into you Aws account or if you don’t have one you can easily create it [here](https://aws.amazon.com/resources/create-account/). It is very simple and super fast to create an AWS account.

![Image description](./Images/console.png)

Once you are in the AWS console, go to services and search for Amazon Sumerian.

![Image description](./Images/aws_console.png)


When the Sumerian editor loads click on create new scene.

![Image description](./Images/Sumerian_Editor.png)

Enter a name for your scene then hit enter then it will take you to the Sumerian Editor.

![Image description](./Images/sumerian%20editor.png)

In the editor click on import asset and upload this [file](https://github.com/bahrain-uob/VoiceMate/blob/master/Voice_To_Sign/VoiceMate-bundle.zip)


![Image description](./Images/bundle%20upload.png)

After you import the bundle then you need to add Cognito Id. You can create one by clicking [here](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/quickcreate?templateURL=https:%2F%2Fs3.amazonaws.com%2Fsumerian-cfn-templates%2FTranscribeStreamingLexPollyExampleTemplate.yml&stackName=AmazonSumerianTrascribeStreamingStack)

![Image description](./Images/cloud%20formation%20stack.png)

Copy the Cognito Id that you generated and paste it into the Sumerian scene.

![Image description](./Images/cognito%20id.png) 
 
Add the Cognito id in your scene...

![Image description](./Images/entering%20cognito%20id.png)

After that download the lambda function file by clicking [here](https://github.com/bahrain-uob/VoiceMate/blob/master/sumerian-text-process-function.zip)

Go to the Aws [lambda console](https://console.aws.amazon.com/lambda/home?region=us-east-1#/functions)

![Image description](./Images/Screen%20Shot%202020-11-11%20at%2010.22.18%20AM.png)

Click on Create function 

![Image description](./Images/Screen%20Shot%202020-11-11%20at%2010.25.03%20AM.png)

Keep the default setting and give any name to your function.

![Image description](./Images/Screen Shot 2020-11-11 at 2.54.44 PM.png)

Then click on create function.

In the Function code section, expand the Code entry type drop-down list, and then choose Upload a .ZIP file.

![Image description](./Images/Screen Shot 2020-11-11 at 2.58.49 PM.pngg)

After you have uploaded the zip file successfully, copy the ARN number.

![Image description](./Images/Screen Shot 2020-11-11 at 3.02.42 PM.png)

Go back to the sumerina editor. First in the entities pannel click on the character and then in the script pannel click on the edit scipt icon (pencil icon).

![Image description](./Images/Screen Shot 2020-11-11 at 3.10.01 PM.png)

It will open a new window. 

Once you’re done with setting up the CloudFormation stack, importing the bundle, creating a lambda function and setting up the Cognito ID. You will be presented with the following scene.

![Image description](./Images/importing%20bundle.png)

There are two main entities in this scene:

-	The HTML entity labeled “AudioTranscription”
-	The 3D character model

### AudioTranscription

The scripts on this component handle the audio transcription to text. 
  
### Character Pack

The 3d model in the scene has an animation component attached and has all the states linked to its respective animation clips. The model was purchased and animations were created in Blender, a popular 3D modelling software. Any other software can be used as well.

The 3d model also has a script component attached. The “AnimationScript” handles all the logic to play animations based on the transcribed text.

![Image description](./Images/importing%20bundle%202.png)

Once you are done modifying the scene then you have to publish it ,choose Publish in the upper-right corner, and then choose Host privately.

![Image description](./Images/publishing.png)



## Pricing

As part of the AWS Free Tier, you can get started with Amazon Sumerian for free. Upon sign-up, new customers can create up to a 50MB published scene that receives the equivalence of 100 views (5GB) per month, for the first 12 months.

You are charged for the total size of the 3D assets you upload and store in Sumerian at the rate of $0.06 per GB per month.

[Amazon Sumerian Pricing](https://aws.amazon.com/sumerian/pricing/)

## References

The feature of amazon transcribing service was added using this [tutorial](https://docs.sumerian.amazonaws.com/articles/hands-free-voice-transcription/)

The 3D model was purchased from [here]()


