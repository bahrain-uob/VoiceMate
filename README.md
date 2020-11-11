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

Log into you Aws account or if you don’t have one you can easily create it [here](https://aws.amazon.com/resources/create-account/)

![Image description](./Images/console.png)

Once you are in the console, go to services and search for Amazon Sumerian.

![Image description](./Images/aws_console.png)


When the Sumerian editor loads click on create new scene.

![Image description](./Images/Sumerian_Editor.png)

Enter a name for your scene then hit enter then it will take you to the Sumerian Editor.

![Image description](./Images/sumerian%20editor.png)

In the editor click on import asset and upload this [file](https://github.com/gray-guy/AWS_VoiceMate/blob/master/Voice_To_Sign/VoiceMate-bundle.zip)


![Image description](./Images/bundle%20upload.png)

After you import the bundle then you need to add Cognito Id. You can create one by clicking [here](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/quickcreate?templateURL=https:%2F%2Fs3.amazonaws.com%2Fsumerian-cfn-templates%2FTranscribeStreamingLexPollyExampleTemplate.yml&stackName=AmazonSumerianTrascribeStreamingStack)

![Image description](./Images/cloud%20formation%20stack.png)

Copy the Cognito Id that you generated and paste it into the Sumerian scene.

![Image description](./Images/cognito%20id.png) 
 
Add the Cognito id in your scene...

![Image description](./Images/entering%20cognito%20id.png)

After that download the lamda function file by clicking [here]()

Go to the Aws [lambda console](https://console.aws.amazon.com/lambda/home?region=us-east-1#/functions)

![Image description](./Images/Screen%20Shot%202020-11-11%20at%2010.22.18%20AM.png)

Click on Create function 

![Image description](./Images/Screen%20Shot%202020-11-11%20at%2010.25.03%20AM.png)
