This works on the idea of Image-to-Image translation.

The simplest model for Image-to-Image translation could be an encoder- decoder based network and use a discriminator to enforce encoder-decoder network to produce images that are similar to the source domain.

![[Reconstruction based Domain Adaptation.png]]

Then, train a source domain classifier based on source data.
![[Reconstruction based Domain Adaptation 2.png]]

During inference, the image of the target domain will be transmitted to the source domain classifier trained for prediction.
![[Reconstruction based Domain Adaptation 3.png]]

Encoder: Compresses target image into a feature vector that captures essential details, ignoring domain-specific details.

Decoder: Reconstructs the image to match the source domain's style, ensuring it fits the source domain.

Source Classifier: Classifies the style-matched image using a model trained on source domain data.