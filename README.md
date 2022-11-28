# QTM350
Description of how to replicate our final project of using AWS Rekognition

## Blog Post Link: https://github.com/luoannie00/QTM350/blob/main/QTM350_Final_Project.ipynb

## Introduction
Currently, the Covid-19 pandemic has resulted in considerable changes to our way of life compared to the era before the pandemic. While wearing masks became a norm in daily life for individuals, it inconveniences us to read and understand others’ facial expressions of emotions under the cover of a mask. According to Grenville and Dwyer, without wearing masks, confidence was significantly greater, with the impact evident for all emotions except anger. It demonstrates that emotion recognition is altered by face masks, but that the effectiveness varies depending on the expressed mood.

This project seeks to identify the flaw in the Rekognition algorithm and determine the effect of wearing masks and glasses in determining the facial expression of emotions(positive vs negative) of individuals. Based on previously mentioned research, we hypothesize that while wearing both masks and glasses would yield the lowest confidence statistics, wearing neither of them would yield the highest confidence results. In comparing wearing a mask and weaning glasses, wearing a mask should present a lower confidence statistic.

## Objectives
We hypothesized that wearing glasses and/or masks would impair the effectiveness of AWS Rekognition on recognizing human faces. More specifically, we believe that wearing masks would make it much more difficult for the machine to detect whether one is smiling, and wearing masks and/or glasses would affect Rekognition's ability to predict the emotions of the faces.

So we did a controlled experiment using photos of our group members, where everything is the same within each set of photos except wearing masks and/ or glasses or not.

## Data Collection 
All data used has been uploaded to a public S3 bucket on AWS named "qtm350-final-project." If there are any access issues, we have also uploaded our photo data under "Photos" folder on this github page. 

We took 4 photos of each of our group members. One with glasses, one with mask, one with both glasses and mask, and one with neither.

1. no mask, no glasses 
2. no mask, with glasses 
3. with mask, no glasses 
4. with mask, with glasses

This dataset allowed us to do a controlled experiment on performance of Rekognition algorithm with and without factors of wearing masks and wearing glasses. Since we have 7 group members, we took a total of 7 x 4 = 28 pictures. So our dataset have 28 observations for our input data.

Our output data would be two tables demonstrating attributes of Rekognition that we selected to analyze. Please see conclusion for further explanation of our output data.

Note: we have included our code that created an S3 bucket and moved photos to this bucket.

## Code
Our annotated codes are under "QTM350_Final_Project.ipynb" file, where we looked at facial attributes of whether one's smiling, whether one's wearing glasses, and one's emotion using Rekognition. We also found similarities among faces of the same person using Rekognition.

## Architecture
<img width="763" alt="IMG_4343" src="https://user-images.githubusercontent.com/90478858/204379441-84816236-9879-422d-bfae-42cc900c6158.PNG">
We uploaded images to AWS S3 bucket. We then use sagemaker's jupyter notebook feature with kernal Python3 to connect to S3 and retrieve the photos as input data. We then use Rekognition ML API to analyze the photos and store our analysis into transformed output data. We also did some visualizations for each of our resulting data frames to showcase our result. Finally, we pushed our final blog with contexts, descriptions, codes and walkthroughs, visualizations, and conclusions to this github repo.

## Conclusion
In the "Smile" attribute, we found that wearing glasses and/ or mask impaired Rekognition's ability to detect smiles. In peng's example, where Peng smiled in all four photos, Rekognition only detected the smile in the photo with neither glasses nor mask. 
In the "Glasses" attribute, we found that Rekognition is tempted to recognize faces with only masks on as having glasses on, since a lot of photos ended with a 3: with mask, no glasses were classified as "True" for "Glasses" feature.
In the "Emotion" attribute, we can also see the effects of wearing masks on Rekognition, since many photos numbered 3 and 4: with mask, no glasses and with mask, with glasses, respectively, were mistakenly detected as "FEAR."
Finally, we found that the similarity attribute of Rekognition is pretty strong, since we saw minimal influences of wearing glasses and/or masks on similarity among faces of the same person.
In general, we can see the trend that certain features of Rekognition has been affected by the person in the photo wearing glasses and/ or masks, while some features were not very much affected.
