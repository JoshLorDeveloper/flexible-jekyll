---
layout: post
title: "PictureStory"
date: 2018-12-18 12:00:30 +0300
description: An iOS app that lets people effortlessly combine photos to create videos showing their change and growth over time
img:  PictureStory1.jpg
tags: [App, Swift, AI, iOS]
link: true
center-background: true
---

An iOS app that lets people effortlessly combine photos to create videos showing their change and growth over time. Import images that you already have or take new photos every day. Stitch selected photos together to build beautiful time-lapse videos of yourself, family, pets, friends, and environment.  Unlike other apps on the App Store, PictureStory centers your images so that you don't have to worry about taking the perfect photo every time. The app enables seamless transitions between photos, and produces stunning artistic videos in seconds. 

<figure class="tableFigure">
    <img width=300 src="/assets/img/PictureStoryAI.png">
    <figcaption class="tableCaption">Showcases how app uses facial recognition algorithms for alignment</figcaption>
</figure> 

PictureStory centers images through an Artifical Intelligence algorithm that first identifies one's facial location, rotation, and size. Then, it uses matrix tranformations to align each image with a predefined anchour image. Through this process, I strngthened my understanding of artificial intelligence, as well as learned about mathmatical transformations and the processes involved with mapping one set of points onto another across coordinate systems.

Further challenges included ensuring that memory usage did not increase as the number of photos stored in the app increased. Pictured below is first before I used background threads to optimize storage, and second the memory usage after video creation was moved to backgoround threads and the overall app underwent memory optimization. Despite this process, being extremely laborious I learned a great deal about synchronization and memory manaagement. Now, all images load on background threads as predicted by users scrolling. They are then released soon after exiting the screen. Furthermore, in terms of video creation itself, the process is done by dispatching to background threads, and tracking the video creation process on foreground threads. In terms of memory management, images are released from temporary memory directly after they have been placed in the video, allowing near linear space efficiency during video creation.

<div class="postTable">
    <figure class="column2">
        <img src="/assets/img/PictureStoryStorage1.png">
        <figcaption>Memory utilization during video generation without optimization</figcaption>
    </figure>
    <figure class="column2">
        <img src="/assets/img/PictureStoryStorage2.png">
        <figcaption>Memory utilization during video generation with optimization</figcaption>
    </figure>
</div>
To further optimize, I am starting to cache all image recognition data locally. This allows for the app to let users choose between multiple faces for centering in a single photo and  significantly decreases video build time. The major problem that I have had with this approach is ensuring that image capture times remain low. Such requirement have forced more image processing and computation to background threads, creating memory leak and error catching problems, where the app must ensure that if the user exits the app while processing a new image, the image is not lost.

Download link: [https://apps.apple.com/uy/app/picturestory/id1447016136](https://apps.apple.com/uy/app/picturestory/id1447016136)
<br />
<br />

---

### Example video:
This is a video that was generated and aligned entirely by PictureStory.

<iframe width="560" height="760" src="https://www.youtube.com/embed/3TGDe9xo2EE" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="display:block;margin: 0 auto;border-radius:5px;"></iframe>
<br />

---

### Screenshots Gallery:

<div class="postTable">
    <figure class="column3">
        <img src="/assets/img/PictureStory1.jpg">
        <figcaption>Promotional Graphic that showcases the PictureStory iOS phone application icon </figcaption>
    </figure>
    <figure class="column3">
        <img src="/assets/img/PictureStory2.jpg">
        <figcaption>The main video editing page in the PictureStory app containing video settings</figcaption>
    </figure>
    <figure class="column3">
        <img src="/assets/img/PictureStory3.jpg">
        <figcaption>The face selection screen where users can select what face to use for centering</figcaption>
    </figure>
    <figure class="column3">
        <img src="/assets/img/PictureStory4.jpg">
        <figcaption>The home page of the PictureStory app, where users can select a story/video to edit</figcaption>
    </figure>
    <figure class="column3">
        <img src="/assets/img/PictureStory5.jpg">
        <figcaption>Inside the app there are also options to add dates to images and have daily notifications</figcaption>
    </figure>
    <figure class="column3">
        <img src="/assets/img/PictureStory6.jpg">
        <figcaption>The app's internal camera page, allowing users to take photos with a guiding overlay</figcaption>
    </figure>
</div>