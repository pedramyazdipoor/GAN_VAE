## **Virtual generation of pavement crack images**

This is a full implementation of this [article](https://doi.org/10.1016/j.engappai.2021.104376) by me.\
The dataset used in this project can be found [here](https://github.com/juhuyan/CrackDataset_DL_HY/tree/master/BoxLevel_Detection).

Our goal is to develop an image generation model that we can use to augment our dataset by generating new but similar crack images to real ones in order to improve       Faster R-CNN performance in detecting pavement cracks.
The architecture of the image generation model is pretty creative. We first train a variational autoencoder to learn latent encodings of real crack images; Then we put decoder away and latent vectors obtained from the variational encoder are used to do sampling. This sampling is essential for providing randomness needed to generate new images. After that, we feed the sampled vector as input to the DCGAN model. Finally, we do the same thing with discriminator as we did to the decoder!\\
![image](https://github.com/user-attachments/assets/cc87e314-98b1-4920-ad3f-8f893e7fee5d)



