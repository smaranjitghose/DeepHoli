# DeepHoli 🎨💦
An deep learning application to simulate holi affect for your group pictures!

## **Holi** 🎊💃

![](https://github.com/smaranjitghose/DeepHoli/blob/master/images/holi_1.jpg)
```Photo by Maxime Bhm on Unsplash```


[Holi](https://en.wikipedia.org/wiki/Holi) is an auspisious full moon day 🌕 celebrated predominantly in India and other parts of the world that signifies the arrival of spring 😎 and the end of winter ❄ . Additionaly it serves to be an occasion for ushering love😍 , forgeting old differences ⚔ , forgiving each other 🙏 , reparing shattered connections 🔨 and most importantly meeting each other 🙋‍♀️🙋‍♂️ and spending a gala time together.

![](https://github.com/smaranjitghose/DeepHoli/blob/master/images/holi_2.jpg)
```Photo by Sandra Seitamaa on Unsplash```


Popularly known as the __Festival of Colors__, a vital part of the celebration is characterized people smearing each other's face with dry powered colors called _abir_ or _gulal_. This can be also extended to a water fight where people use water guns(_pichkaris_) or colored water filled ballons against each other to end up like a canvas of colors while enjoying the entire activity in playfullness

## The motivation 

As popular and noble cause that Holi serves, it poses certain environmental concerns such as:
- wastage of huge amounts of water that could be used otherwise for sustaining life 🚫😒
- pollution of water bodies 🌊❗
- contanimation of the ecosystem 🦌🌼 involved 
- health issues due to hazardous chemicals💀 used in the powders 

So, it sprung upon that can we use deep learning to emulate how it would be for us to play Holi without actually having done so?💡

## So lets see what we can do: 🧠

We make use of the concept of **Photorealistic Image Style Transfer** 📸 here, which means to transfer the style of one image called the ```style image``` to another image called the  ```content image``` ,while making sure that the original structure and detail outline of the content image is intact as well as the resultant image resembles a real image that would have been shot by camera

While several methods have been proposed over the years, here we shall use [NVIDIA'S A Closed-form Solution to Photorealistic Image Stylization](https://research.nvidia.com/publication/2018-09_A-Closed-form-Solution) for our purpose 🔥

## An overview of what's happening under the hood: 🔍

The entire process comprises two steps:


![](https://miro.medium.com/max/691/0*FdRWiIH6w9OistOF.png)

1. Stylization (F1): Generating a ``stylized image`` with visible distortions by applying a whitening and coloring transform to the deep features extracted from the ```content image(Ic)``` and  ```style image(Is)```.


2. Smoothing(F2): Suppressing the distortion in the ```stylized image``` by applying an image smoothing filter to make sure that it retains the spatial information of the ```content image(Ic)```

![](https://miro.medium.com/max/1117/0*fC8M7XY3gFifIpYi.png)


#### **Stylization(F1)**

For photorealistic stylization an approach called PhotoWCT is used which is an architectural fine tuning of [WCT](https://arxiv.org/abs/1705.08086)

A synopsis for the training method for WCT is:

1. Do the task of image reconstruction through VGG architecture.
2. Based on the image of the trained VGG Net input Ic, the output of the last layer of the Encoder is proposed.
3. Based on the image of the trained VGG Net input Is, the output of the last layer of the Encoder is proposed.
4. Wc conversion of Ic based on Is information is called A.
5. Use A as the input of the Decoder. After the Decoder, it will output the style converted picture.

![](https://miro.medium.com/max/1312/0*8dkFm5QPDd538iEm.png)

For WCT, when the encoder does Maxpooling, the size of the image is doubled but the spatial information is destroyed and Unsampling is used to resote it

For PhotoWCT Unpooling (green) is used to replace the original Upsampling (pink)

![](https://github.com/smaranjitghose/DeepHoli/blob/master/images/stylization_1.png)

##### **Smoothning(F2)**:

The pixel affinities in the ``content image`` are used to smoothen the output of ```PhotoWCT```  to ensure that the stylization effect between the surrounding pixels is identical while the style conversion of the overall image remains intact as much as possible

For describing pixel similarities, all the pixels are represented as nodes in a graph and an affinity matrix is defined as:

![](https://miro.medium.com/max/1145/0*_gC1BA_c4kt-OIGY.png)

For the optimization, we take care of a smoothening and fitting component:
![](https://github.com/smaranjitghose/DeepHoli/blob/master/images/smoothning_1.png)

## Enough of literature🥱🥱 ..Show me the work 🏗!

#### Requirements:
1. python must be installed
2. The following dependencies should be installed:
- numpy
- Pillow
- keras
- scipy

#### Input:

- Our Content Image:

![](https://github.com/smaranjitghose/DeepHoli/blob/master/images/content.png)

- The Holi Style:

![](https://github.com/smaranjitghose/DeepHoli/blob/master/images/style.png)

#### Output:

- Happy Holi:

![](https://github.com/smaranjitghose/DeepHoli/blob/master/images/output.png)

#### Comparisions:

![](https://github.com/smaranjitghose/DeepHoli/blob/master/images/amalgated.png)




## Credits 👏👏

This repo is merely a reimplementation of the following work catering to the Holi scenario and complete credit goes to:

**Closed-form Solution to Photorealistic Image Stylization-Yijun Li, Ming Yu Liu, Xueting Li, Ming Hsuan Yang, Jan Kautz** 

- [Research Paper](https://eccv2018.org/openaccess/content_ECCV_2018/papers/Yijun_Li_A_Closed-form_Solution_ECCV_2018_paper.pdf) 📃
- [GitHub Repo](https://github.com/NVIDIA/FastPhotoStyle) 👨‍💻👩‍💻

[Copyright (C) 2018 NVIDIA Corporation. All rights reserved.Licensed under the CC BY-NC-SA 4.0 license](https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode)
