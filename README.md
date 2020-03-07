# DeepHoli 🎨💦
An deep learning application to simulate holi for your gang of friends!

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

#### An overview of what's happening under the hood: 🔍

The entire process comprises two steps:


![](https://miro.medium.com/max/691/0*FdRWiIH6w9OistOF.png)

1. PhotoWCT (F1): Generating a ``stylized image`` with visible distortions by applying a whitening and coloring transform to the deep features extracted from the ```content image(Ic)``` and  ```style image(Is)```.


2. Photorealistic Smoothing(F2): Suppressing the distortion in the ```stylized image``` by applying an image smoothing filter to make sure that it retains the spatial information of the ```content image(Ic)```

![](https://miro.medium.com/max/1117/0*fC8M7XY3gFifIpYi.png)


## Credits 👏👏

This repo is merely a reimplementation of the following work catering to the Holi scenario and complete credit goes to:

**Closed-form Solution to Photorealistic Image Stylization-Yijun Li, Ming Yu Liu, Xueting Li, Ming Hsuan Yang, Jan Kautz** 

- [Research Paper](https://eccv2018.org/openaccess/content_ECCV_2018/papers/Yijun_Li_A_Closed-form_Solution_ECCV_2018_paper.pdf) 📃
- [GitHub Repo](https://github.com/NVIDIA/FastPhotoStyle) 👨‍💻👩‍💻

[Copyright (C) 2018 NVIDIA Corporation. All rights reserved. Licensed under the CC BY-NC-SA 4.0 license] (https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode)
