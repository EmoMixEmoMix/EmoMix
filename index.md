<!-- <p align="justify">
In this post, we show the demo of EmoMix: Emotion Mixing via Diffusion Models for Emotional Speech Synthesis
</p> -->

## Abstract
<p align="justify">
There has been significant progress in emotional Text-To-Speech (TTS) synthesis technology in recent years. However, existing methods primarily focus on the synthesis of a limited number of emotion types and have achieved unsatisfactory performance in intensity control. To address these limitations, we propose EmoMix, which can generate emotional speech with specified intensity or a mixture of emotions. Specifically, EmoMix is a controllable emotional TTS model based on a diffusion probabilistic model and a pre-trained speech emotion recognition (SER) model used to extract emotion embedding. Mixed emotion synthesis is achieved by combining the noises predicted by diffusion model conditioned on different emotions during only one sampling process at the run-time. To control the intensity, we apply the Neutral and specific primary emotion noise combined in varying degrees. Experimental results validate the effectiveness of EmoMix for synthesizing mixed emotion and intensity control. 
</p>

## Model Architecture

![]({{ site.url }}/assets/image/overall.png) 
The overview architecture for EmoMix and the green part represents the extended sampling process of mixed emotion synthesis at run-time. The dotted arrows are only used during training. The SER mdoels are pre-trained and their parameters are frozen.

## Experiment
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



### Primary Emotion Synthesis

<table>
    <tr>
	<th> Target Text</th>
	<th> Emotion </th>   
	<th> Ground Truth</th>
        <th> proposed </th>
    </tr>

    <tr>
        <th> And vowed he'd change the pigtail's place </th>
	<th> Surprise </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/base_emo/[000048][0013_001578][G].wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/base_emo/[000048][0013_001578][P].wav" type="audio/mpeg"></audio> </th>
    </tr>
	
    <tr>
        <th> In which fox loses a tail and its elder sister finds one </th>
	<th> Sad </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/base_emo/[000001][0012_001090][G].wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/base_emo/[000001][0012_001090][P].wav" type="audio/mpeg"></audio> </th>
    </tr>
	
    <tr>
        <th> Do you know the lid opens </th>
	<th> Happy </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/base_emo/[000040][0013_000924][G].wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/base_emo/[000040][0013_000924][P].wav" type="audio/mpeg"></audio> </th>
    </tr>
	
    <tr>
        <th> They found a cow grazing in a field </th>
	<th> Angry </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/base_emo/[000029][0015_000444][G].wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/base_emo/[000029][0015_000444][P].wav" type="audio/mpeg"></audio> </th>
    </tr>
</table>





### Primary Emotion Intensity Control
We apply Neutral and primary mixture to control primary emotion intensity.
<table>
    <tr> 
	<th> Emotion </th>
	<th style="5px;word-wrap;word-break"> Weak</th>
        <th style="5px;word-wrap;word-break"> Medium </th>
        <th style="5px;word-wrap;word-break"> Strong </th>
    </tr>

	<tr>
	<th> Neutral-Surprise </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/primary_intensity/sur-1.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/primary_intensity/sur-2.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/primary_intensity/sur-3.wav" type="audio/mpeg"></audio> </th>
        </tr>
	
	<tr>
	<th> Neutral-Happy </th>	
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/primary_intensity/hap/n-h1.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/primary_intensity/hap/n-h2.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/primary_intensity/hap/n-h3.wav" type="audio/mpeg"></audio> </th>
        </tr>

   	<tr>
	<th> Neutral-Sad </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/primary_intensity/sad-1.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/primary_intensity/sad-2.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/primary_intensity/sad-3.wav" type="audio/mpeg"></audio> </th>
        </tr>
	
	<tr>
	<th> Neutral-Angry </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/primary_intensity/ang-1.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/primary_intensity/ang-2.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/primary_intensity/ang-3.wav" type="audio/mpeg"></audio> </th>
        </tr>
</table>



### Mixed Emotion Synthesis


<table>
    <tr> 
	<th style="5px;word-wrap;word-break"> Base</th>
        <th style="5px;word-wrap;word-break"> Mixed-in</th>
	<th style="5px;word-wrap;word-break"> Mixture</th>
    </tr>
     <tr> 
	<th style="5px;word-wrap;word-break"> Outrage</th>
        <th style="5px;word-wrap;word-break"> Angry</th>
	<th style="5px;word-wrap;word-break"> Surprise</th>
    </tr>
     <tr> 
	<th style="5px;word-wrap;word-break"> Disappointment</th>
        <th style="5px;word-wrap;word-break"> Sad</th>
	<th style="5px;word-wrap;word-break"> Surprise</th>
    </tr>
     <tr> 
	<th style="5px;word-wrap;word-break"> Excitement</th>
        <th style="5px;word-wrap;word-break"> Happy</th>
	<th style="5px;word-wrap;word-break"> Surprise</th>
    </tr>	
</table>

<table>
    <tr> 
	<th> Mixed Emotion </th>
	<th style="5px;word-wrap;word-break"> Base</th>
        <th style="5px;word-wrap;word-break"> Mixed-in</th>
	<th style="5px;word-wrap;word-break"> Mixture</th>
    </tr>
	<tr>
	<th> Excitement </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/mix/hap-sup111.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/mix/hap-sup222.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/mix/hap-sup333.wav" type="audio/mpeg"></audio> </th>
        </tr>
	
	<tr>
	<th> Disappointment </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/mix/sad-sup1.wav" type="audio/mpeg"></audio> </th>        
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/mix/sad-sup3.wav" type="audio/mpeg"></audio> </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/mix/sad-sup2.wav" type="audio/mpeg"></audio> </th>	
        </tr>
	
	<tr>
	<th> Disappointment </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/mix/sad-sup11.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/mix/sad-sup33.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/mix/sad-sup22.wav" type="audio/mpeg"></audio> </th>
        </tr>
	
	<tr>
	<th> Outrage </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/mix/ang-sup1.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/mix/ang-sup3.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="EmoMix_Audio/mix/ang-sup2.wav" type="audio/mpeg"></audio> </th>
        </tr>
	


   	
</table>




