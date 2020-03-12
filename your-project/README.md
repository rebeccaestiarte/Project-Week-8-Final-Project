<img src="https://bit.ly/2VnXWr2" alt="Ironhack Logo" width="100"/>

# Analysis of Brainwaves behaviour during Mindful Meditation
*[Rebecca Estiarte]*

*[Data Analysis, Barcelona & 11/03/2020]*

## Content
- [Project Snapshot](#project-snapshot)
- [Main Hypotheses](#Main Hypotesis)
- [Dataset](#dataset)
- [Cleaning](#cleaning)
- [Statistical Analysis](#analysis)
- [Model Training and Evaluation](#model-training-and-evaluation)
- [Conclusion](#conclusion)
- [Future Work](#future-work)
- [Workflow](#workflow)
- [Links](#links)

## Project Snapshot
Analysis of Mindful Meditation Practice impact over electroencephalogram (EEG) using brainwaves data acquired through headband sensor.

## Main Hypotesis
The hipotesis is that the practice of Mindful Meditation affect the brainwaves activity even for inexperienced meditators. I also want to prove that the change in brainwaved frequency pattern experienced in meditation is beneficial for the practicioner.

## Dataset
I collected all the data used in this project using the Muse wearable brain sensing headband, manufactured by InteraXon. I was able to measure the brain activity of a sample group via 4 electroencephalography (EEG) sensors placed on the headband. As Interaxon has retired from the market his Software Developer Kit (SDK), I used a third party app named "Mind Monitor" to retrieve the data. The app is able to process the EEG data and output a single combined average value for the five absolute brain wave values. It can output the data into Excel compatible CSV (Comma Separated Values) files that I directly uploaded into a Google Drive folder from my smartphone.

## Cleaning
The first step was removing all columns that where out of the scope of the project. Secondly, I removed all rows that contained null values which corresponded to the timestamps the headband failed to record. I also created a column named "Activity", that had a value of 0 for the control sessions and 1 for the meditation sessions. This information will be used as a target for the machine learning model that I will be describing further on. I saved all dataframes of normal sessions into a list and the dataframes of meditation sessions into another. Finally, I computed the aggregated mean of all dataframe of normal sessions into a unique dataframe, and did the same with the meditation sessions.

## Statistical Analysis
I used a deductive analysis to conduct the process. I started with comparing, on both individual and aggregate level, the behaviour of brainfrequencies during meditation vs control to find patterns and differences. This process resulted three main observations: 

* The average brain frequencies on a normal state range between 0 and 1 while the frequencies during meditation range from -0.5 and 0.5, which is the optimal range (the range the frequencies are supposed to move in for our brain activity to perform efficiently). 
* Alpha Waves during meditation sessions clearly predominates over the other waves. When Alpha predominates most people feel at ease and calm. It has been proved that a predominant Alpha frequency is the most efficient way to run the brain, as it does not require a too high amount of energy.
*  Gamma Waves seams to peak more ofter during meditation.

I used hypotesis testing to confirm that the above conjectures could be proved with statistical significance. The results where positive for all but the last observation.

## Model Training and Evaluation

The second part of my project consisted in building a Machine Learning Model and test it. This algorithm aimed to identify if a person is in state on meditation or not based on the brainfrequencies the headband registers. It could be used to give real time feedback to the user during a meditation session by alerting the user when its mind is wondering. The first step was processing the data to train the model: firstly, I divided each recording session into four quartiles to see the correlation of each with the meditation activity. Thereupon I merged the dataframes into a unique dataset. I then splitted the data into features and target and I fit the model with the quartiles that had higher correlation: Q2 and Q3. As my previous analysis showned, those quartiles were the most relevant as the person began entering a state of relaxation after 5 minutes into the meditation session. I fitted the data into different machine learning algohritms (Logistic Reggressor (LR), Random Forest Regressor (RFR) and K nearest neighbor (KNN)) and compared the accuracy scores of the predictions of each. I used crossed validation to avoid overfitting. After testing the models with different parameters, I choosed Logistic Regression as the best classifier, which an accuracy of 100% and a cross validation score average of 75%. I could consider myself satisfied with those results considering that I had only 16 columns to train and test the algohritm. More data is required to get better accuracy with machine learning. 

## Conclusion
* Meditation is useful to make people brainwaves work at optimal levels.
* Meditation induce us into a state of calm and focus, as alpha brainwaves become stronger than other waves during the practice.
* Gamma waves are not proved to behave differently during meditation for amateur practioners.

## Future Work
Due to time constrains, I was unable to collect enough data to make further observation. Also, I was unable to get a sample which size and diversity was high enough to minimize bias. Also, a greater dataset would allow me to achieve higher accuracy on the machine learning model.

## Workflow
I started the project by realizing the experiment, which I describe in detail on the Main Notebook, with the participants. While I was collecting the data, I started building the functions that will allow me to automatize the import and cleaning of the dataset, as well as the graphs I used to analyse the data. This way, I could update my model with each new session (dataset) imported. It was a necessary work to optimize time, as I had to conduct the experiments in different days and times to reduce the bias. I did not make any observations untill I finished collecting the data. Once the experiments were done, I could analyse the results and make my observations. I hypotesis tested the observations and detailed my conclusion. After that, I began reprocessing the data to fit into the machine learning algohritm. I conducted many modifications to the train data untill I was satisfied with the model performance.

## Links

[Repository](https://github.com/)  
[Slides](https://slides.com/)  
[Trello](https://trello.com/en)  
