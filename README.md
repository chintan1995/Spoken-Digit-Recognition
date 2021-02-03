# Spoken-Digit-Recognition
<pre>
Input - speech signal, output - digit number

1. Reading the dataset. and Preprocess the data set. Detailed instrctions are given below.
2. Training the LSTM with RAW data
3. Converting to spectrogram and Training the LSTM network
4. Creating the augmented data and doing step 2 and 3 again.  
</pre>

# <font color='purple'>**Output Observations**</font>
<ul>
<li>The data we have is in <b>Audio format</b>. To work on audio data, we need to convert it into numeric data by <b>sampling</b> it using a sampling rate.</li>
<li>As any audio is sequential in nature, we can make use of <b>LSTM</b> in this case. The Audios are of various lengths, however LSTM cannot work with variable length input sequences. Hence, after doing an EDA, we found that 99% of the audios are of 0.8 seconds, and so we decided to keep the max sequence length as the 0.8 seconds. Converting into the samples, it comes out to be 17640.</li>
<li>We tried 4 different models, which are described as follows
    <ul>
        <li><b>Using Raw data:</b> We directly used the Raw samples from the audio. The work flow is as follows,<br>
        <a href="https://imgur.com/a/P6kGhh4/">
         <img alt="Raw data" src="https://i.imgur.com/AHfdECy.png"
         width="200" height="300">
      </a> <br>
      The raw data gave us the micro F1 score of 0.125, which is a poor score, and is almost like a random guess. 
        </li>
        <li><b>Using Spectogram data:</b> We used the Spectrogram data from the audio. The work flow is as follows,<br>
        <a href="https://imgur.com/a/BrVJkZM/">
         <img alt="Spectrogram data" src="https://i.imgur.com/yBEDu8i.png"
         width="250" height="500">
      </a><br>
      As we didn't get good enough F1 score using only the raw data, now we used the spectrogram data of the audios. The spectrogram data gave us the micro F1 score of 0.9507, which is a very good score.</li>
        <li><b>Augmenting Raw data:</b> We used the Augmented Raw samples from the audio. The work flow is as follows,<br>
        <a href="https://imgur.com/a/OmlUH06/">
         <img alt="Augmented Raw data" src="https://i.imgur.com/PwWXZYZ.png"
         width="200" height="400">
      </a><br>
      We tried to augment the raw data in this model. It gave us the micro F1 score of 0.1004, which is a poor score, and is almost like a random guess. </li>
        <li><b>Augmenting Spectogram data:</b> We used the Augmented Spectrogram data from the audio. The work flow is as follows,<br>
        <a href="https://imgur.com/a/FUCowY2/">
         <img alt="Augmented Spectrogram data" src="https://i.imgur.com/M6EIra4.png"
         width="250" height="500">
      </a><br>
      As we didn't get good enough F1 score using only the augmented raw data, now we augmented the spectrogram data of the audios. The augmented spectrogram data gave us the micro F1 score of 0.9392, which is a very good score.</li>
    </ul>
</li>
<li><b>Why does Spectrogram give better results?</b>
    <ul>
        <li>We saw that Spectrogram data of the audio is giving us better results as compared to using plain raw samples from the audio. This is because te spectrogram gives us a rich set of information/features such as pitch difference, volume, overtone, etc. which can help us better differentiate what is said in the audio. Whereas, the audio sampling (raw data) does not give us any of that information, and is just a series of numbers with no inherant features. </li>
    </ul>
</li>
</ul>
