# Chatbot
In this repo  i have implemented a seq2seq model to create a generative
chatbot.According to the results (the printed answers to user questions) there
is a lot to improved.Maybe if we trained the model to more epochs and increase
the embedding size to 1024 we ll have better results.Another possible way to
imrove the model is use categorical crossentropy as loss function, or the rmsprop
optimizer.

## 1. Description of this repo
A chatbot is a software that provides a real conversational experience to the
user. There are closed domain chatbots and open domain (generative) chatbots.
Closed domain chatbot is a chatbot that responses with predefined texts. A
generative chatbot generates a response as the name implies.In this report we
will generate a response based on the training corpus. We are going to use the
encoder-decoder (seq2seq) model for this approach using the metalwoz dataset.

## 2.Dataset
Meta-Learning Wizard-of-Oz (MetaLWOz) is a dataset designed to help develop
models capable of predicting user responses in unseen domains. It can improve
dialog systems, such as those used in voice assistants, to help users accomplish
tasks such as booking a flight. This dataset is particularly suited for metalearning
dialog models or fine-tuning models with transfer-learning approaches.
This dataset aims to reduce the amount of data required to train domain-specific
dialog systems and it is one of the first datasets designed with meta-learning
dialog models in mind.
This large dataset was created by crowdsourcing 37,884 goal-oriented dialogs,
covering 227 tasks in 47 domains. Domains include bus schedules, apartment
search, alarm setting, banking, and event reservation. Each dialog was grounded
in a scenario with roles, pairing a person acting as the bot and a person acting as
the user. Each pair were given a domain and a task, and instructed to converse
for 10 turns to satisfy the user’s queries. For example, if a user asked if a bus
stop was operational, the bot would respond that the bus stop had been moved
two blocks north, which starts a conversation that addresses the user’s actual
need.

## 3.Methodology

### 3.1 Data Preparation and Pre-Proccesing
The first thing , we do is to prepare the dataset by tranforming the raw data
to pairs of answers and questions.We cleaned the data by tranforming all text
to lower and then by making simple tranfromatios like ”i’m” to ”i am”.We kept
only small questions (with length less than 20) and their answers.After that we
implemented tokenization and vectorization and zero padding.
### 3.2 Creation of LSTM, Encoder and Decoder Model
LSTM is a special kind of RNN that is capable of learning long-term dependencies.
Encoder-Decoder model contains two parts- encoder which takes the vector
representation of the input sequence and maps it to an encoded representation
of the input. This is then used by the decoder to generate output.
Train and Save Model
We trained the model with 50 epochs and a batch size of 20, while word embedding
size was set to 512, we took sparse cross-entropy as our loss function
and optimizer used was AdamOptimizer. We got the best results with these
parameters. We trained and tested our model on Colab using GPU. The training
accuracy obtained was approximately 94% and validation accuracy of about
85%.
### 3.3 Testing
Finally, the user can input questions and bot will reply to the answer of the
Question. The results obtained shows that there is much room for improvement.

## 4.Example of Final Ouptut
Below is some chats with the generative model. 
User:Hey
Chatbot: hello how may i help you
User: who is spiderman
Chatbot: do you want to know the score of last weeks
User: yes
Chatbot:okay i have gone ahead and set the playlist alarms now ¡OUT¿ from
there anything else
User: are you serious?
Chatbot:yes i cant fetch you that information right now
User:is the information true?
Chatbot:i will not provide you for tomorrow to you is it
User: okey thank you
Chatbot:you are welcome
User:can i ask you something?
Chatbot: yes
User:can you book me a table for four?
Chatbot:i am sorry but i am unable to recognize that book
User:can you make a reservation?
Chatbot:unfortunately but i cant
User:what can you do?
Chatbot:i can help with alarms
User:set an alarm for five a.m
Chatbot:sound or vibrate
User:sound
Chatbot:what sound rooster sound
User:whatever you like
Chatbot:cheers

