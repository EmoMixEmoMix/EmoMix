<p align="justify">
In this post, we show the demo of QI-TTS: Questioning Intonation Control for Emotional Speech Synthesis
</p>

## Abstract
<p align="justify">
Recent expressive text to speech (TTS) models focus on synthesizing emotional speech, but some fine-grained styles such as intonation are neglected. In this paper, we aim to better transfer and control intonation to further deliver the speaker's questioning intention while transferring emotion from reference speech. We propose a multi-style extractor to extract style embedding from two different levels. While the sentence level represents emotion, the final syllable level represents intonation. For fine-grained intonation control, we use relative attributes to represent intonation intensity at the syllable level. To reduce the overlap of information between style embedding and content embedding, an adversarial content predictor with gradient reversal layer is adopted. Experimental results validate the effectiveness of our proposed method for improving intonation expressiveness in emotional speech synthesis.  
</p>

## Model Architecture
<!-- <center class="half">
    <img src="assets/image/fig1.jpg" width="300"/>
    <img src="assets/image/fig2.jpg" width="300"/>
</center>       <p>&nbsp;</p> 
<p align="center">Figure.1 The architecture of the functional digestive metabolic network,</p> -->

<table>
    <tr>
        <td ><center><img src="assets/image/fig1.jpg"/> </center></td>
        <td ><center><img src="assets/image/fig2.jpg"/> </center></td>
    </tr>
	<tr>
		<th> (A) DMN </th>
		<th> (B) FDMN </th>
<!--         <td>(A) DMN </center></td>
        <td >(B) FDMN </center> </td> -->
    </tr>

	
</table>
<p align="center">Figure.1 (A) The architecture of the functional digestive metabolic network (DMN). (B) The architecture of the functional digestive metabolic network (FDMN).</p>


<!-- ### General Digestive Metabolic Network

![Model Architecture ](assets/image/fig1.jpg)
<p align="center">Figure.1 The architecture of the general digestive metabolic network.</p>

### Functional Digestive Metabolic Network

![Spectrograms](assets/image/fig2.jpg)
<p align="center">Figure.2 The architecture of the functional digestive metabolic network.</p> -->

## Experiment
### Dataset
We select the ESD dataset~\cite{zhou2021seen} to perform the model training. We use English part of the ESD database spoken by 10 native English (5 male and 5 female) in five emotions: Neutral, Angry, Happy, Sad, and Surprise. Importantly, we add "statement" and "question" labels with the help of K-means method similar to Into-TTS~\cite{lee2022into}. After adding ”statement” and ”question” labels there are 1440 statements and 310 questions (160 normal questions and 150 declarative questions) for each speaker on average. Besides, declarative questions are mainly distributed in the emotion of surprise. We follow the data partition given in ESD dataset: training set (1500 utterances), reference set (150 utterances), and test set (100 utterances).


<p>&nbsp;</p> 

<script>
function pauseOthers(ele) {
    $("audio").not(ele).each(function (index, audio) {audio.pause();});
}
</script>

<style>
.main-content table {
    display: inline-table;
}
table {
    table-layout:fixed;
    width: 100%;
    overflow: hidden;
}
#player{
    width: 100%;
}
</style>



### Parallel Style Transfer
In parallel style transfer, the synthesizer is given an audio clip matching the text it’s asked to synthesize (i.e. the reference and target text are the same).

<table>
	<CAPTION>Reference/Target Text: The rainbow is a division of white light into many beautiful colors.</CAPTION>
    <tr>
	<th> Ground Truth</th>
        <th> Fastspeech + GST </th>
        <th> proposed </th>
    </tr>
	
    <tr>
        <th> text1 </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/audios/Ground_Truth/30/0.mp3" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/audios/Tacotron2/30/0.mp3" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/audios/Tacotron2_x-vec/30/0.mp3" type="audio/mpeg"></audio> </th>
    </tr>
</table>



### Non-Parallel Transfer
In non-parallel style transfer, the TTS system must transfer prosodic style when the source and target text are completely different. Below, contrast the monotonous prosody of the baseline with examples of long-form synthesis with a narrative source style.
<table>
	<CAPTION>Reference Text: When the sunlight strikes raindrops in the air, they act as a prism and form a rainbow.</CAPTION>
    <tr>
	<th> Reference Audio</th>
	<th> Target Text</th>
	<th> proposed</th>
    </tr>
    <tr>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/audios/Ground_Truth/30/0.mp3" type="audio/mpeg"></audio> </th>
    </tr>
</table>	

### Intonation Intensity Control

<table>
	<CAPTION>Table.4 The Intonation Intensity Evaluation</CAPTION>
    <tr> 
        <th> Text </th>
	<th style="5px;word-wrap;word-break"> Intensity = 0.3 (Most Weak)</th>
        <th style="5px;word-wrap;word-break"> Intensity = 0.6 (Medium) </th>
        <th style="5px;word-wrap;word-break"> Intensity = 0.9 (Most Strong) </th>
    </tr>
    <tr>
        <th> Andy what's the gyre and to gimble? </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0011_001406-Surprise-G.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0011_001406-Surprise-MG1.5.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0011_001406-Surprise-MG2.wav" type="audio/mpeg"></audio> </th>
    </tr>

	<tr>
        <th> A nauseous draught? </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0019_001410-Surprise-MG1.5.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0019_001410-Surprise-MG.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0019_001410-Surprise-MG2.wav" type="audio/mpeg"></audio> </th>
        </tr>
	
	<tr>
        <th> On the twenty second of last march? </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0019_001409-Surprise-MG.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0019_001409-Surprise-MG1.5.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0019_001409-Surprise-MG2.wav" type="audio/mpeg"></audio> </th>
        </tr>

	<tr>
        <th> At the end of four? </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0017_001419-Surprise-MG1.5.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0017_001419-Surprise-MG.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0017_001419-Surprise-MG2.wav" type="audio/mpeg"></audio> </th>
        </tr>

</table>
