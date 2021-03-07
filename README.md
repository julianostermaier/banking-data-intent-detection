# banking-data-intent-detection

## Steps in this Notebook

1. Analyze the Dataset
2. Clean and preprocess data for Neural Network
3. Create an iterable dataset
4. Build and 5. train a Recurrent Neural Network to get good Classification results

## More about the Dataset I used

Dataset is composed of online banking queries annotated with their corresponding intents. (*Efficent Intent Detection with Dual Sentence Encoders; Iñigo Casanueva and Tadas Temčinas and Daniela Gerz and Matthew Henderson and Ivan Vulić*, https://arxiv.org/abs/2003.04807)

* Dataset consists of roughly 10 000 training and 3 000 testing samples each of them labeled with one of the 77 intents
* The samples consist of different customer requests e.g. *I made a mistake and need to cancel a transaction* which is then labeled with the corresponding intent, in this case *cancel_transfer*
* The challanging part about the dataset: "*The single-domain focus of BANKING77 with a large number of intents makes it more challenging. Some intent categories partially overlap with others, which requires fine-grained decisions [...]*" (*Efficent Intent Detection with Dual Sentence Encoders; Iñigo Casanueva and Tadas Temčinas and Daniela Gerz and Matthew Henderson and Ivan Vulić*)

## Goal
Goal of my work is to create a Neural Network that classifies the Intents, which then can be used to create a Rule Based Chatbot that handles customer requests.

## Results

I was able to train a Recurrent Neural Network with LSTM - Cells to classify the intents based on the user requests in the dataset.

![](https://github.com/julianostermaier/banking-data-intent-detection/blob/main/accuracy-over-time.png)
![](https://github.com/julianostermaier/banking-data-intent-detection/blob/main/confusion-matrix.png)

The confusion matrix shows, that some categories are recognized with a high accuracy of more than 80 %. Still, there are some categories that our recurrent neural network is not picking up on, probably because they are hard to distinguish from each other. That's why the accuracy for some categories might be so low.

![](https://github.com/julianostermaier/banking-data-intent-detection/blob/main/accuracy-other-models.png)

Considering the algorithms used in the mentioned paper, with the highest test accuracy of about **94 %** (BERT model), are very complex, our simple RNN did fairly good with it's test accuracy of around **67 %**.
