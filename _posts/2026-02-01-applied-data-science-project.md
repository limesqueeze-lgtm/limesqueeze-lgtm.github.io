---
layout: post
author: Jeshua Nelson Lim - 8454144M
title: "Applied Data Science Project Documentation"
categories: ITD214
---
## Project Background
Business scenario: Group2 Global Enterprise is planning to set up a hotel in Portugal. Apart from internal resource management, hotels also experience wastage of resources due to external factors in the form of guest behaviour such as booking cancellation or mismatch in guest expectations & preferences. 
As the hotel will be based in Portugal, guests will likely be tourists from Europe.
#
Business Goals: Support the establishment of the hotel by lowering the wastage of resources which could arise from focusing on factors that are not as important. 
Business Objective 1: To predict whether customers will cancel their bookings & factors affecting it.
Business Objective 2: Identify key themes in reviews to prioritise operations and guide establishment of the new hotel
## Work Accomplished
Document your work done to accomplish the outcome

## Data Preparation
### Collect Inital Data
Obtain data from relevant database of guest booking and stay records of hotels based in Portugal. 
Collect or scrape online reviews of target customer groups ie. tourists and travellers from Europe as tourists to Portugal are primarily from Europe.

<img width="1449" height="418" alt="image" src="https://github.com/user-attachments/assets/53fe7a6d-2783-4d97-a275-408a779d7ad0" />
Booking dataset is based on real world data from hotels in Portugal and HRAST utilises reviews from hotel reviews in Europe, which is the target group of travellers.
Hotel booking dataset has 119,390 rows and HRAST has 23,113 rows.

### Clean
<img width="798" height="309" alt="image" src="https://github.com/user-attachments/assets/50473475-10a1-435d-a9ed-41b33a0e825c" />

Check for missing rows: Nil

Remove redundant "ID" column

Check for duplicated rows

> Rationale is to not inflate certain topics

> From 23,113 to 23,105 rows

### Preprocessing
<img width="943" height="857" alt="image" src="https://github.com/user-attachments/assets/92996479-fbe1-43a5-9a81-63128ab821e2" />
Conducted in Python.
#
Selected Model Technique: Latent Dirichlet Allocation (LDA)

Evaluate LDA model by finding optimal number of topics:

1) Perplexity is the score of how confused/surprised the model is. Low perplexity means that the model has found clear and distinct topics.

2) Coherence rates the interpretability of topics. Determines how logical a topic is.

3) Manual/human Interpretability of topics

### Modelling
#### Model building
<img width="867" height="224" alt="image" src="https://github.com/user-attachments/assets/5628f841-a853-44d0-b4ea-cc81656fd971" />

<img width="912" height="847" alt="image" src="https://github.com/user-attachments/assets/a515c85b-15b6-406f-9de1-da280994ed01" />

<img width="886" height="333" alt="image" src="https://github.com/user-attachments/assets/7a0a4a60-d8f6-48f6-9324-43943228a4e0" />

<img width="436" height="292" alt="image" src="https://github.com/user-attachments/assets/bbb93032-8312-49f5-9d34-e8ff24aa3c29" />

<img width="1028" height="793" alt="image" src="https://github.com/user-attachments/assets/9ee9c844-b61d-4bd8-80e9-6ab29a00f2cb" />

k=12 had best perplexity value

k=18 had best coherence score
#
Utilise pyLDAvis for visualisation
<img width="648" height="199" alt="image" src="https://github.com/user-attachments/assets/c52ffd85-578f-4452-9991-2cb88c1cd519" />
#
#### k=12 topics
<img width="1176" height="627" alt="image" src="https://github.com/user-attachments/assets/0d328682-ca3d-4f27-add1-83b033a57416" />
<img width="824" height="747" alt="image" src="https://github.com/user-attachments/assets/b6688d6b-b814-4d70-ae69-528555a6bdf1" />

#### k=18 topics
<img width="1225" height="653" alt="image" src="https://github.com/user-attachments/assets/b472fb41-40da-421c-b1f8-134e3b5c0797" />
<img width="775" height="1125" alt="image" src="https://github.com/user-attachments/assets/8835dfe3-6591-4392-8d14-b8f619ea9c7c" />

There are still some difficulty in interpreting topics.

Non-domain specific words like “nice”, “bit”, “well”, “really”, “would”... 

Some topics appear to be similar, repeated words.

Based on intertopic distance map, topics appeared to be not so clustered but still have some overlap.

Perplexity might not be the best measure.

### Model Tuning
Update stopword list to further remove noise

Coherence value improved. 
<img width="1638" height="169" alt="image" src="https://github.com/user-attachments/assets/91b3bb9d-c9db-4bd7-b68b-84bd0af37b35" />
<img width="1277" height="475" alt="image" src="https://github.com/user-attachments/assets/e51b4654-1a7f-4a4c-a3c1-09b532d94e8b" />
<img width="1737" height="885" alt="image" src="https://github.com/user-attachments/assets/89637676-be70-4504-852d-de7127ed9201" />

### Further tuning
Added more stopwords, expanded range of K to find drop-off.
<img width="1394" height="593" alt="image" src="https://github.com/user-attachments/assets/2f7cdc18-94aa-4c67-86c8-39f95c2e801e" />

### Model Assessment
#### k=12
<img width="1910" height="718" alt="image" src="https://github.com/user-attachments/assets/ddde5f2a-69a5-4d6d-a6c0-ebe764f4b433" />

#### k=15
<img width="2195" height="911" alt="image" src="https://github.com/user-attachments/assets/bd8f4ef3-6429-4d3f-a52f-185ce088e690" />

#### k=18
<img width="2276" height="1125" alt="image" src="https://github.com/user-attachments/assets/f7315fa6-3c18-40af-8798-6329ca014868" />


#### k=22
<img width="2308" height="1133" alt="image" src="https://github.com/user-attachments/assets/d6d4fcf2-8911-44a1-919f-d924009304fd" />

### Model Comparison
Of the three, k=15 gave the best model per the visualisation

K=18 and K=22 had very clustered topics although they performed better at coherence.

All models had similar coherence values

The higher the K, the more difficult it became to interpret the topics.

<img width="546" height="296" alt="image" src="https://github.com/user-attachments/assets/7a377a05-6d96-48e1-911d-85cae88cb41e" />
<img width="1742" height="509" alt="image" src="https://github.com/user-attachments/assets/268664b7-3762-4607-92e5-0c3d0ca59a15" />


### Evaluation

At this stage, k=15 was chosen.

There were still some overlaps but topics were mostly distinguishable.
<img width="1667" height="835" alt="image" src="https://github.com/user-attachments/assets/f98a3fbb-e86f-4541-adb3-c57c15e38131" />

Topics were colour coded and grouped according to similar themes.

<img width="2008" height="1152" alt="image" src="https://github.com/user-attachments/assets/5216fd0b-9f43-4fa1-8a84-db3dd14dc220" />
Grouping was not based entirely on pyLDAvis, domain knowledge came into play to group them manually.

Interpret the topcs and draw insights

<img width="1847" height="1362" alt="image" src="https://github.com/user-attachments/assets/64cd4306-195f-42ad-b112-1eeae614b509" />

<img width="1847" height="1181" alt="image" src="https://github.com/user-attachments/assets/0e519e54-0bad-4267-96ef-7a550e209310" />

<img width="1847" height="1316" alt="image" src="https://github.com/user-attachments/assets/3f45c315-15ce-49ed-b4a5-bd3db41eaf10" />

### Review of the model
<img width="1862" height="189" alt="image" src="https://github.com/user-attachments/assets/3799590c-746e-4627-9afc-fd54f3052fd2" />
Topics identified are interpretable and rational.

Practical solutions can be implemented based on the findings allowing focus on what hotel guests are concerned with for day-to-day operations. 

Avoid misallocation of resources into tacky features & poor design of the hotel and neglecting the important aspects.

Recommendations also seek to return positive reviews and reduce negative ones in order to attract new guests as well as return guests. 



## Recommendation and Analysis
### Establishing hotel (design and building)
Overall, the strongest theme appears to be in relation to the rooms.

Invest in high-quality bed and pillows.

Toilets should have good pressure showers with heater option.

Provide WiFi and room-service.

Ensure room space is designed efficiently and not too small.

Ensure proper air-condition and ventilation.

Location of the hotel is crucial.

Need to source for a location where the hotel is not too secluded.

Must have alternatives for food in the vicinity.

Distance to areas of interests & attractions should be considered.

Should invest in active soundproofing measures (eg. double glazed windows, greenery) if passive soundproofing design is restricted.

Pool should be easily accessible to guests.
#
### Operations of the hotel
Prioritise cleanliness & maintenance of the hotel.

Invest in good quality fixtures to last longer.

Incorporated into design of hotel to ensure ease of cleaning and maintenance.

Increase frequency of cleaning.

In-house food quality must be decent and value-for-money.

Maintain pool to be fit-for-use.

Invest in training of staff.

Maintain service quality and teach soft-skills.

Staff should be friendly and responsive to guest requests.
#
### Identify business issues not addressed earlier
For Hotel Reviews, can train Sentiment Analysis model to classify pos vs neg reviews of the hotel after hotel has begun operations and reviews start coming in. This way, the hotel can monitor brand reputation and also identify what needs improvement.
#
### Limitations and future improvements
For topic modelling, only LDA model was used. 

Could utilise transfer learning such as using BERTopic and Top2Vec to see if can reduce preprocessing steps and produce better topics. Will require more time to find a suitable pre-trained model that is comparable with our problem (ie. reviews of hotels instead of other models trained on tweets or movie reviews).

Did not tweak Alpha & Beta Hyperparameters in LDA.

Initially too reliant and tunnel vision on perplexity

Range of K was also limited initially as it was based on trial and error.

Expanded the range of k: 8 to 26

<img width="211" height="295" alt="image" src="https://github.com/user-attachments/assets/d1c2df70-dc8e-49a6-8ad2-9a85f643b676" />
<img width="458" height="359" alt="image" src="https://github.com/user-attachments/assets/642924cb-2984-4790-8ae2-b5d8aee881fb" />

Coherence had indeed improved further past k=22.

However, having more topics could affect interpretability. 

## AI Ethics
Discuss the potential data science ethics issues (privacy, fairness, accuracy, accountability, transparency) in your project. 



## Source Codes and Datasets
Upload your model files and dataset into a GitHub repo and add the link here. 
[ITD214_cleaned_reviews.xlsx](https://github.com/user-attachments/files/25591143/ITD214_cleaned_reviews.xlsx)

