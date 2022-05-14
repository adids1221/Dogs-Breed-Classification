# Dog Breed Classification #
This project is a final project for data science course at Holon Institute of Technology

## About ##
Dog breed Classification project is made under the guidelines of the ‘Introduction to data science’ course as a part of computer science bachelor studies.
The idea for the project came after brainstorming since one of the main requirements of the project was scraping/crawling the data, using pre-made datasets was restricted.

The goal of the project is to create a pipeline that firstly cleans the images data from images without dogs or images with high intensity, and then classifies the breed of the dog in the image.

## Contents of notebooks: ##
-- Crawlers:
We created 5 different crawlers, but we mainly used the Pond5 and iStocks crawlers.

-- Data cleaning:
1. ResNet 50
2. IQR cleaning

-- Classifier

## Project planing ## 
* Data acquisition (using scraping, crawling and API)

## Data Cleaning ## 
Data cleaning pipeline:
<img width="1047" alt="Screen Shot 2022-02-12 at 14 19 17" src="https://user-images.githubusercontent.com/72259329/153711053-79f2a9d0-bfd4-4152-a58a-fc7dd505fac9.png">

**We started by detecting images without dogs using ResNet50:**

<img width="999" alt="Screen Shot 2022-02-12 at 14 22 49" src="https://user-images.githubusercontent.com/72259329/153711155-c7836542-4f53-44d9-842d-19623e80cadd.png">

**After ResNet we found out that our data contains many drawings, which may create problems during classification, thus, we chose to detect the drawings using Entropy. As soon as we started to look for an entropy value threshold from which drawings will be detected, we faced another problem:
Images with an uniform background, tend to give as low entropy value as drawings gave.
Thus, in the calculation of the entropy, we eliminated the _most common value_ from each image (which, in most cases represents the background in images with a uniform background.**

<img width="780" alt="Screen Shot 2022-02-12 at 14 20 32" src="https://user-images.githubusercontent.com/72259329/153711087-4de24d1f-70a7-4038-84bb-7f1d1f067ee0.png">

**At third step, we calculated the avarage outliers amount for each class. How we did that?
1.Calculate the mean of an image and flatten it.
2.Calculate the IQR 40-60 of that image.
3.Sum all IQRs values of all images of the class and devide by number of images of that class 
After we had the avarage outliers of a class we decided to eliminate some of the classes due proccessing power limitaion. 
We took into account the avarages distribution and the distribition of images count of each class.**


<img width="1020" alt="Screen Shot 2022-02-12 at 14 20 49" src="https://user-images.githubusercontent.com/72259329/153711097-8bf24375-b94d-4d83-8491-6b0a72876df6.png">

At sixth step, We calculated and plotted the intensitiy distribution of the images for each class and also for the whole data itself after cleanning to check if we made a good job (the overall intesnitiy decreased)

<img width="763" alt="Screen Shot 2022-02-12 at 14 21 08" src="https://user-images.githubusercontent.com/72259329/153711108-9e43b5f7-492c-41ab-96dc-17e4ccc316ca.png">

<img width="966" alt="Screen Shot 2022-02-12 at 14 21 18" src="https://user-images.githubusercontent.com/72259329/153711115-67bc1903-9a92-419d-be21-d45015e74114.png">
<img width="862" alt="Screen Shot 2022-02-12 at 14 21 29" src="https://user-images.githubusercontent.com/72259329/153711120-43977d31-43c4-42f6-951b-8beb543256f5.png">

## Classification ##
**At first, we hit 67% + overfitting:**

<img width="924" alt="Screen Shot 2022-02-12 at 14 36 10" src="https://user-images.githubusercontent.com/72259329/153711614-387ac5e3-d9e2-46fe-a9f6-15cca5790f72.png">

**Then, we did more epochs and added some augmentation:**

<img width="961" alt="Screen Shot 2022-02-12 at 14 37 17" src="https://user-images.githubusercontent.com/72259329/153711648-bdff4110-a86f-458c-844e-d2a43901e772.png">

<img width="930" alt="Screen Shot 2022-02-12 at 15 03 00" src="https://user-images.githubusercontent.com/72259329/153712515-a6dca899-46bc-49c9-b32c-7992817caa90.png">



**Project's log: **
<img width="946" alt="Screen Shot 2022-02-12 at 14 39 55" src="https://user-images.githubusercontent.com/72259329/153711709-6de9973b-bdd0-405b-b9ea-f06ce6f22b8c.png">


* Machine Learning
* Deep learning
* CNN
* Image classification (using Tensorflow)

## Contributing ##
Project status: Finished.  
Author: adids1221, yuvalnsn

In this project all the data came from scrapping and the crawling is used for educational purpose only.  
This data is NOT used for distribution of any kind or for any other purpose rather than for educational.  
Copyright for the images goes to: Flicker, Pond5, iStock images.

This project is licensed under the terms of the MIT license and protected by Udacity Honor Code and Community Code of Conduct. See license and disclaimer.
