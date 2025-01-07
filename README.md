## **Virtual generation of pavement crack images**

This is a full implementation of this [article](https://doi.org/10.1016/j.engappai.2021.104376) by me.\
The dataset used in this project can be found [here](https://github.com/juhuyan/CrackDataset_DL_HY/tree/master/BoxLevel_Detection).

Our goal is to develop an image generation model that we can use to augment our dataset by generating new but similar crack images to real ones in order to improve Faster R-CNN performance in detecting pavement cracks.

The architecture of the image generation model is pretty creative. We first train a variational autoencoder to learn latent encodings of real crack images; Then we put decoder away and latent vectors obtained from the variational encoder are used to do sampling. This sampling is essential for providing randomness needed to generate new images. After that, we feed the sampled vector as input to the DCGAN model. Finally, we do the same thing with discriminator as we did to the decoder!

Image below is from [article](https://doi.org/10.1016/j.engappai.2021.104376):

![image](https://github.com/user-attachments/assets/894d690f-079e-400b-ae77-0c3cc782c54c)

After training the VAE + DCGAN model, we fine-tuned the famous Faster R-CNN object detection model in order to find cracks on images. We tested it in two scenarios; in our first try we fine-tuned it on real images, in our last we did it on a mixed of real images and generated images to see if we can see improvements in Average Precision. 

We evaluated our generative model even further by two known metrics: Inception score(IS) and Fréchet inception distance(FID). You can read more about them [here](https://ahujaniharika95.medium.com/inception-score-is-and-fr%C3%A9chet-inception-distance-fid-explained-2bc28a4faea7).




