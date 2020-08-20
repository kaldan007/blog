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
![]({{ site.baseurl }}/images/transkribus/block_diagram.png)
## Training data collection
Since most of our pechas are in distinct handwriting, we always try to train dedicated model for each pecha to get better transcription. We always train our models with training and validation data of ratio 8:2. While collecting training and validation data for the model, we tends to divide the process into two main parts. Those are layout analysis and getting respective trasncription.
### Layout annalysis

### Transcript
## Model Training
## Transcripting using Model
## Post Processing the Model output
