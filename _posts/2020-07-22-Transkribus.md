---
toc: true
layout: post
description: Handwritten Text Recognition in Tibetan manuscript using Transkribus.
categories: [markdown, Esukhia]
title: How to use Transkribus to transcribe Tibetan pecha(pering) effectively?
---

## What is Transkribus?
Transkribus is a software deticated for transcripting text from handwritten or printed old manuscript's images. It enable users to train dedicated model for recognising text in manuscripts. Shout out to H2020 Project READ[(Recognition and Enrichment of Archival Documents)](https://read.transkribus.eu/) for funding the transkribus project. To know more about transkribus project itself and explore more about the use case, you can refer transkribus webpage [here](https://transkribus.eu/wiki/images/7/77/How_to_use_TRANSKRIBUS_-_10_steps.pdf). I will be assuming that you have pretty good idea about how does transkribus work.

## Our Use case
In our case, we have plenty of rare and old manuscripts waiting for digitisation. Most of our manuscript are in pering layout format. Pering is the most common pecha(manusript) layout format found in early days. An example of pering layout page is shown below.(image_link) We faced many challanges while trying to transcripting those pechas using transkribus in normal way. We figured out that we can do some interference to get better results. Hence this article is about what kind of interference that we have done in order to get better model and better transcription. 
## Block diagram
Here is the block diagram of the whole procedure that we follow.


![]({{ site.baseurl }}/images/transkribus/block_diagram.png "Block diagram")


## Training data collection
Since most of our pechas are in distinct handwriting, we always try to train dedicated model for each pecha to get better transcription. We always train our models with training and validation data of ratio 8:2. While collecting training and validation data for the model, we tends to divide the process into two main parts. Those are layout analysis and getting respective trasncription.

### Layout annalysis
It is the part where segmentation of lines in image take place. Transkribus has multiple ways of doing the task design specifically for some general manuscripts layout. We tried mutliple layout analysis models among which newspaper model out perform the rest in our case. Hence we choosed it. But still newspaper model dosen't produce perfect layout analysis. In order to get better layout analysis, we have written a  script to tune layout analysis as per our requirement.

#### What we tried:
- We ran existing models without adjustment. Since our segmentation is inaqurate, hence our recognitions results turnout to be noisy and disordered borderlines are considered as text.

 - We ran newspaper LA model and try to correct manually. It was a failure as the method was very time and labour expensive(1-2 hr. per page).

 - We traced detailed boxes from scratch thinking that LA model will learn from our traced images. Unfortunately, it didn't and whole afford became in vien.
 
#### Our Solution:
- First we ran **Newspaper Layout Analysis** on our images.
- We download the resultant files in Traskribus format.
- In transkribus file format, we ran our script on **Page** folder.
- Our script will bring all the lines into order, remove noise and unify broken segments of a line into one segment.
- We upload the updated **Page** folder along with image files and meta data files to the respective Transkribus Collection.
- We ran our HTR model on that file.
- After that we download the resultant file.
- Resultant file goes under a post processing script which reorder alignment whereever needed. A segment is consider noise if length of text in a segment is less than a threshold. Noise segments are ignored in order to get better result. 

### Transcript
## Model Training
## Transcripting using Model
## Post Processing the Model output
