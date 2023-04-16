---
title: Fastai Prac Guitar Classifier
emoji: 🏢
colorFrom: purple
colorTo: blue
sdk: gradio
sdk_version: 3.24.1
app_file: app.py
pinned: false
license: apache-2.0
---

# Guitar Type Image Classifier
### This is an image classifier app that identifies a guitar's type based on its image. This was done as a quick mini-project to try out the FastAI+Gradio+HF Spaces stack. The model itself has been fine-tuned from [ResNet18](https://arxiv.org/abs/1512.03385) using the FastAI API.

## List of guitar types in this app's scope:
1. [Acoustic Bass Guitar](https://en.wikipedia.org/wiki/Acoustic_bass_guitar)
    - [What it sounds like](hhttps://www.youtube.com/watch?v=smxaH-GTW1w)
2. [Archtop Guitar](https://en.wikipedia.org/wiki/Archtop_guitar)
    - [What it sounds like](https://www.youtube.com/watch?v=piKSZsJsJyM)
3. [Classical Guitar](https://en.wikipedia.org/wiki/Classical_guitar)
    - [What it sounds like](https://www.youtube.com/watch?v=tTqYmit4dtA)
4. [Electric Bass Guitar](https://en.wikipedia.org/wiki/Bass_guitar)
    - [What it sounds like](https://www.youtube.com/watch?v=smxaH-GTW1w)
5. [Electric Guitar](https://en.wikipedia.org/wiki/Electric_guitar)
    - [What it sounds like](https://www.youtube.com/watch?v=YKHwkJzcJR4)
6. [Flat-top Guitar](https://en.wikipedia.org/wiki/Flat_top_guitar)
    - [What it sounds like](https://www.youtube.com/watch?v=jBpBh1yFZO0)

## Assumptions and Caveats:
- Semi-acoustic guitars of all types have been kept in the acoustic category.
- There was some manual data cleaning done between data augmentation and model fine-tuning. The details are described in the [train.py](train.py) script.

## Observations:
- The most commonly confused category pairs are **acoustic bass:classical** and **classical:flat-top**. This makes sense because apart from the headstock and the strings themselves, these 3 categories are largely similar. Higher resolution images for training should help the model in doing a better job of distinguishing these categories.
- The fine-tuning works well despite being given less than 200 images per class and 5 training epochs.

## Using the app:
1. The app can be accessed at https://huggingface.co/spaces/rdat/fastai-prac-guitar-classifier. Add an image to the input area and click submit to get the model's inference along with probability percentages.
2. The train.py script can be executed with the appropriate config parameters to train (fine-tune) a new model.

## Next Steps:
1. Add a component to the Gradio interface that lets the user play a sample of the instrument when its corresponding example image is selected.
2. Experiment with more recent ResNet models and supply them with more data for fine-tuning.
3. Perform more extensive hyperparameter tuning.
4. Add performance metrics to the README file. 

#### Notes:
##### 1. All external links fall under the Creative Commons license.
##### 2. Check out the HF Spaces configuration reference at https://huggingface.co/docs/hub/spaces-config-reference
