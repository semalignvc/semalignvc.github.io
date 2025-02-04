# SemAlignVC: Enhancing zero-shot timbre conversion using semantic alignment

## Abstract

> Zero-shot voice conversion (VC) synthesizes speech in a target speaker’s voice while preserving linguistic and paralinguistic content. However, timbre leakage—where source speaker traits persist—remains a challenge, especially in neural codec and LLM-based VC, where quantized representations entangle speaker identity with content. We introduce SemAlignVC, an architecture designed to prevent timbre leakage using SemAlign, a novel method that aligns text and audio representations to ensure speaker-independent semantic encoding. This disentangled representation conditions an autoregressive transformer for high-fidelity conversion without explicit speaker embeddings. Experiments show SemAlignVC significantly reduces timbre leakage, outperforming baselines in speaker timbre similarity, intelligibility, and naturalness, making it a robust, privacy-preserving, and generalizable VC solution.

<style type="text/css">
    .tg {
    border-collapse: collapse;
    border-color: #9ABAD9;
    border-spacing: 0;
  }

  .tg td {
    background-color: #EBF5FF;
    border-color: #9ABAD9;
    border-style: solid;
    border-width: 1px;
    color: #444;
    font-family: Arial, sans-serif;
    font-size: 14px;
    overflow: hidden;
    padding: 0px 20px;
    word-break: normal;
    font-weight: bold;
    vertical-align: middle;
    horizontal-align: center;
    white-space: nowrap;
  }

  .tg th {
    background-color: #000000;
    border-color: #9ABAD9;
    border-style: solid;
    border-width: 1px;
    color: #fff;
    font-family: Arial, sans-serif;
    font-size: 14px;
    font-weight: normal;
    overflow: hidden;
    padding: 0px 20px;
    word-break: normal;
    font-weight: bold;
    vertical-align: middle;
    horizontal-align: center;
    white-space: nowrap;
    padding: 10px;
    margin: auto;
  }

  .tg .tg-0pky {
    border-color: inherit;
    text-align: center;
    vertical-align: top,
  }

  .tg .tg-fymr {
    border-color: inherit;
    font-weight: bold;
    text-align: center;
    vertical-align: top
  }
  .slider {
  -webkit-appearance: none;
  width: 75%;
  height: 15px;
  border-radius: 5px;
  background: #d3d3d3;
  outline: none;
  opacity: 0.7;
  -webkit-transition: .2s;
  transition: opacity .2s;
}

.slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 25px;
  height: 25px;
  border-radius: 50%;
  background: #409cff;
  cursor: pointer;
}

.slider::-moz-range-thumb {
  width: 25px;
  height: 25px;
  border-radius: 50%;
  background: #409cff;
  cursor: pointer;
}

audio {
    width: 160px;
}

/* CSS */
.button-12 {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 6px 14px;
  font-family: -apple-system, BlinkMacSystemFont, 'Roboto', sans-serif;
  border-radius: 6px;
  border: none;

  background: #6E6D70;
  box-shadow: 0px 0.5px 1px rgba(0, 0, 0, 0.1), inset 0px 0.5px 0.5px rgba(255, 255, 255, 0.5), 0px 0px 0px 0.5px rgba(0, 0, 0, 0.12);
  color: #DFDEDF;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
}

.button-12:focus {
  box-shadow: inset 0px 0.8px 0px -0.25px rgba(255, 255, 255, 0.2), 0px 0.5px 1px rgba(0, 0, 0, 0.1), 0px 0px 0px 3.5px rgba(58, 108, 217, 0.5);
  outline: 0;
}

video {
  margin: 1em;
}

</style>


## Subjective Evaluation
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">Source</th>
    <th class="tg-0pky">Timbre reference</th>
    <th class="tg-0pky">KNNVC</th>
    <th class="tg-0pky">HierSpeech++</th>
    <th class="tg-0pky">UniAudio</th>
    <th class="tg-0pky">SemAlignVC</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/input-p258_011_012.wav" type="audio/wav">
      </audio>
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/ref-f_p229.wav" type="audio/wav">
      </audio> 
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/knnvc-p258_011_012-f_p229.wav" type="audio/wav">
      </audio>  
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/hierspeechpp-p258_011_012-f_p229.wav" type="audio/wav">
      </audio>   
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/uniaudio-p258_011_012-f_p229.wav" type="audio/wav">
      </audio>  
   </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/semalignvc-p258_011_012-f_p229.wav" type="audio/wav">
      </audio>
   </td>
  </tr>
  <tr>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/input-p272_013_014.wav" type="audio/wav">
      </audio>
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/ref-f_p240.wav" type="audio/wav">
      </audio> 
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/knnvc-p272_013_014-f_p240.wav" type="audio/wav">
      </audio>  
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/hierspeechpp-p272_013_014-f_p240.wav" type="audio/wav">
      </audio>   
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/uniaudio-p272_013_014-f_p240.wav" type="audio/wav">
      </audio>  
   </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/semalignvc-p272_013_014-f_p240.wav" type="audio/wav">
      </audio>
   </td>
  </tr>
  <tr>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/input-270_011_012.wav" type="audio/wav">
      </audio>
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/ref-m_p256.wav" type="audio/wav">
      </audio> 
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/knnvc-p270_011_012-m_p256.wav" type="audio/wav">
      </audio>  
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/hierspeechpp-p270_011_012-m_p256.wav" type="audio/wav">
      </audio>   
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/uniaudio-p270_011_012-m_p256.wav" type="audio/wav">
      </audio>  
   </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/semalignvc-p270_011_012-m_p256.wav" type="audio/wav">
      </audio>
   </td>
  </tr>
  <tr>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/input-p364_013_014.wav" type="audio/wav">
      </audio>
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/ref-f_p335.wav" type="audio/wav">
      </audio> 
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/knnvc-p364_013_014-f_p335.wav" type="audio/wav">
      </audio>  
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/hierspeechpp-p364_013_014-f_p335.wav" type="audio/wav">
      </audio>   
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/uniaudio-p364_013_014-f_p335.wav" type="audio/wav">
      </audio>  
   </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/semalignvc-p364_013_014-f_p335.wav" type="audio/wav">
      </audio>
   </td>
  </tr>
  <tr>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/input-p304_011_012.wav" type="audio/wav">
      </audio>
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/ref-m_p251.wav" type="audio/wav">
      </audio> 
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/knnvc-p304_011_012-m_p251.wav" type="audio/wav">
      </audio>  
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/hierspeechpp-p304_011_012-m_p251.wav" type="audio/wav">
      </audio>   
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/uniaudio-p304_011_012-m_p251.wav" type="audio/wav">
      </audio>  
   </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/semalignvc-p304_011_012-m_p251.wav" type="audio/wav">
      </audio>
   </td>
  </tr>
  <tr>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/input-p266_013_014.wav" type="audio/wav">
      </audio>
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/ref-m_p271.wav" type="audio/wav">
      </audio> 
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/knnvc-p266_013_014-m_p271.wav" type="audio/wav">
      </audio>  
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/hierspeechpp-p266_013_014-m_p271.wav" type="audio/wav">
      </audio>
    </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/uniaudio-p266_013_014-m_p271.wav" type="audio/wav">
      </audio>  
   </td>
    <td>
      <audio controls>
        <source src="audio/subjective_evals/semalignvc-p266_013_014-m_p271.wav" type="audio/wav">
      </audio>
   </td>
  </tr>
  </tbody>
</table>


## Objective Evaluation


<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">Source</th>
    <th class="tg-0pky">Timbre reference</th>
    <th class="tg-0pky">KNNVC</th>
    <th class="tg-0pky">HierSpeech++</th>
    <th class="tg-0pky">UniAudio</th>
    <th class="tg-0pky">SemAlignVC</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>
      <audio controls>
        <source src="audio/objective_evals/input-LibriVox_en_US_10179.wav" type="audio/wav">
      </audio>
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/ref-LibriVox_en_US_0167.wav" type="audio/wav">
      </audio> 
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/knnvc-LibriVox_en_US_10179-LibriVox_en_US_0167.wav" type="audio/wav">
      </audio>  
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/hierspeechpp-LibriVox_en_US_10179-LibriVox_en_US_0167.wav" type="audio/wav">
      </audio>   
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/uniaudio-LibriVox_en_US_10179-LibriVox_en_US_0167.wav" type="audio/wav">
      </audio>  
   </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/semalignvc-LibriVox_en_US_10179-LibriVox_en_US_0167.wav" type="audio/wav">
      </audio>
   </td>
  </tr>
  <tr>
    <td>
      <audio controls>
        <source src="audio/objective_evals/input-LibriVox_en_US_10018.wav" type="audio/wav">
      </audio>
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/ref-LibriVox_en_US_0125.wav" type="audio/wav">
      </audio> 
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/knnvc-LibriVox_en_US_10018-LibriVox_en_US_0125.wav" type="audio/wav">
      </audio>  
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/hierspeechpp-LibriVox_en_US_10018-LibriVox_en_US_0125.wav" type="audio/wav">
      </audio>   
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/uniaudio-LibriVox_en_US_10018-LibriVox_en_US_0125.wav" type="audio/wav">
      </audio>  
   </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/semalignvc-LibriVox_en_US_10018-LibriVox_en_US_0125.wav" type="audio/wav">
      </audio>
   </td>
  </tr>
  <tr>
    <td>
      <audio controls>
        <source src="audio/objective_evals/input-LibriVox_en_US_0027.wav" type="audio/wav">
      </audio>
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/ref-LibriVox_en_US_0107.wav" type="audio/wav">
      </audio> 
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/knnvc-LibriVox_en_US_0027-LibriVox_en_US_0107.wav" type="audio/wav">
      </audio>  
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/hierspeechpp-LibriVox_en_US_0027-LibriVox_en_US_0107.wav" type="audio/wav">
      </audio>   
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/uniaudio-LibriVox_en_US_0027-LibriVox_en_US_0107.wav" type="audio/wav">
      </audio>  
   </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/semalignvc-LibriVox_en_US_0027-LibriVox_en_US_0107.wav" type="audio/wav">
      </audio>
   </td>
  </tr>
  <tr>
    <td>
      <audio controls>
        <source src="audio/objective_evals/input-LibriVox_en_US_0020.wav" type="audio/wav">
      </audio>
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/ref-LibriVox_en_US_0031.wav" type="audio/wav">
      </audio> 
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/knnvc-LibriVox_en_US_0020-LibriVox_en_US_0031.wav" type="audio/wav">
      </audio>  
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/hierspeechpp-LibriVox_en_US_0020-LibriVox_en_US_0031.wav" type="audio/wav">
      </audio>   
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/uniaudio-LibriVox_en_US_0020-LibriVox_en_US_0031.wav" type="audio/wav">
      </audio>  
   </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/semalignvc-LibriVox_en_US_0020-LibriVox_en_US_0031.wav" type="audio/wav">
      </audio>
   </td>
  </tr>
  <tr>
    <td>
      <audio controls>
        <source src="audio/objective_evals/input-LibriVox_en_US_0036.wav" type="audio/wav">
      </audio>
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/ref-LibriVox_en_US_0092.wav" type="audio/wav">
      </audio> 
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/knnvc-LibriVox_en_US_0036-LibriVox_en_US_0092.wav" type="audio/wav">
      </audio>  
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/hierspeechpp-LibriVox_en_US_0036-LibriVox_en_US_0092.wav" type="audio/wav">
      </audio>   
    </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/uniaudio-LibriVox_en_US_0036-LibriVox_en_US_0092.wav" type="audio/wav">
      </audio>  
   </td>
    <td>
      <audio controls>
        <source src="audio/objective_evals/semalignvc-LibriVox_en_US_0036-LibriVox_en_US_0092.wav" type="audio/wav">
      </audio>
   </td>
  </tr>
  </tbody>
</table>