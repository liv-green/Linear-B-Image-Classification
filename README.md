# Linear-B-Image-Classification

## Linear B
Linear B is the earliest known written form of ancient Greek. It first arose in roughly 1400 B.C. in the Late Bronze Age, before abruptly disappearing from the historical record 200 years later with the collapse of Mycenaean civilization. Lost from memory for over 3000 years, its tablets were finally recovered at the beginning of the 20th century from the ruins of Knossos in Crete, and deciphered by Michael Ventris in 1953. 

## Computer Vision and the Study of Ancient Languages 
In recent years, a number of ancient languages have benefitted from the potential offered by computer vision to automate manual, labour intensive tasks such as transcription and translation, and to generate new insights and perspectives into long debated areas of research. Linear B, however, has largely remained untouched in this activity. 

A number of challenges inhibit the application of computer vision to Linear B. It suffers from a limited data pool, with only circa 5000 tablets that remain to us today, and a significant number of these being badly damaged or burnt. That image data which is available is highly variable in quality, ranging from a small number of state of the art images to others that are barely legible. Image formats are also inconsistent (for example, some tablets are only available as drawings rather than their real life counterparts, whose originals have been lost). All these factors combined have meant that it is hard to produce a quality dataset of sufficient size for a meaningful application of computer vision to Linear B's challenges.   

## Project Aims and Outcomes
### A new dataset for Linear B’s Symbols
This project aims to address the challenges outlined above and presents a new, quality dataset of Linear B’s symbols, the largest and most extensive of its kind, for the purpose of facilitating further research into this field. The dataset contains 7890 images and is made up of 60 different symbols from Linear B’s corpus.

### An Image Classification Model Based on YoloV8
Using this dataset, this project also presents an image classification model based on [YOLOv8](https://docs.ultralytics.com) for Linear B’s symbols, which achieves an accuracy of 99.47%, and aims to be a first step towards handwritten character recognition tooling capable of automating the transcription of Linear B’s tablets.

4 experiments were conducted using a mix of both the pre-trained and un-trained instances of the YOLOv8 model (where pre-trained means an instance of the YoloV8 model trained on ImageNet data, and un-trained means the raw YoloV8 model). The pre-trained and un-trained models were trained first with data augmentation applied, and then with no data augmentation applied. Data was split into train, validation and test files, and all 4 models were trained on 6286 samples; 762 samples were used for validation during training. Training took place over 30 epochs, and a batch size of 16 was used. 

842 test samples were then used to verify accuracy rates of the models. Top 1 accuracy was the principle metric chosen to measure accuracy (i.e. defining an accurate prediction as one where the model output with the highest probability aligns with the correct class label). A comparative analysis of results on this test data, compared with performance on validation data, is shown below. 

|               | Pre-Trained Model with no Data Aug. | Pre-Trained Model with Data Aug.  | Un-Trained Model with Data Aug. | Un-Trained Model with no Data Aug. |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| No. of High confidence correct predictions (>0.90) | 830 | 816  | 798  | 818  | 
| No. of Low confidence correct predictions (<0.90)  | 4  | 14  | 27  | 14  | 
| No. of Incorrect predictions   | 8 | 12  | 17  | 10 | 
| Model Accuracy on Test Data   | 99.05%  | 98.62% | 97.99%  | 98.82% | 
| Model Accuracy on Validation Data   | 98.90%  | 99.47%  | 98.60%  | 98.70%  | 

## How to Use
### Dataset
The full dataset used in this project is contained here. There are 60 classes in total, and significant class imbalance in the dataset, with the largest class (“ja”) containing 351 samples, and the smallest class (“ju”) containing just 16 samples. The mean number of samples per class is 131. To use the data for image classification, it can be downloaded and split into training, test and validation files using the code here. 

The scope of this dataset is limited to Linear B's core syllabograms (symbols that refer to combination sounds, e.g. "ka" or "te"). A small number of syllabograms whose values are complex or uknown, ideograms (shorthand symbols for specific words or concepts), numbers and other elements of writing system are not included. 

### Models
The models were developed, trained and tested in Google Colab – this colab file can be accessed here. 

The models and summary view of their outputs can be accessed here. These models can be downloaded and tested via the colab file referenced above. 

The process behind the construction of the dataset and models, and a detailed analysis of the models’ results can be reviewed here in the accompanying paper, which was presented as an MSc thesis. 
