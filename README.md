# naive-txt2img-api-of-sd

This repository contains an attempt to modify the Automatic1111webui txt2img API to work with other extensions by directly rewriting the program. Although we are aware that directly modifying the code is not ideal, this was done due to our own laziness and lack of knowledge.

## Implementation Details
We tried to use the functions that run behind the scenes when executing txt2img in the webui directly through the API. Since the arguments are difficult to understand, we first executed txt2img in the webui, checked the arguments being passed, and then passed them in the API.

## Usage and Customization
When using this modified version, you will need to change the arguments according to your own use case. These arguments may change even if you are not using the extension that is installed. Although strings and numbers should not cause any issues, additional handling may be required depending on the value passed as an argument. For example, we only supported the controlnet extension, which takes an image as an argument. For other extensions that take an image as an argument, you will need to modify the txt2img2 API.

We have successfully executed LoRA+controlnet, Lora+multicontrolnet, and LoRA+two-shot by only changing the arguments. As a sample, only the LoRA+controlnet notebook is included in this repository.

## Recommended Setup
It is convenient to run the server notebook on Colab with GPU and run the client notebook locally, as images will be saved locally.

## We have now added compatibility with the latest version of controlnet.
Instead of passing the scripts.external_code.ControlNetUnit object, pass [enabled, module, model, weight, image, guidance_end] as arguments to the txt2img2. If you need to modify any specific variables, please update the convert_args function in the txt2img2 API.

## Addition
We've added a new notebook titled 'Extracting_Pose_Estimation_from_Videos_using_MMpose.ipynb' This notebook allows you to obtain videos from YouTube, perform pose estimation using MMpose, and save the resulting pose estimation images to your Google Drive.
