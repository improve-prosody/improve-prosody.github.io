

{:.no_toc}
* toc
{:toc}
## Abstract

Expressive text-to-speech aims to generate high-quality samples with rich and diverse prosody, which is hampered by two major challenges: 1) considering the one-to-many mapping problem, prosodic attributes in highly dynamic voices are difficult to capture and model without intonation; 2) the TTS model should learn a diverse latent space and prevent producing dull samples with a collapsed prosodic distribution. This paper proposes Prosody-TTS, a two-stage TTS pipeline that improves prosody modeling and sampling by introducing several components: 1) a self-supervised learning model to derive the prosodic representation without relying on text transcriptions or local prosody ground-truth, which ensures the model covers diverse speaking voices, preventing sub-optimal solutions and distribution collapse; and 2) a latent diffusion model to sample and produce diverse patterns within the learned prosodic space, which prevents TTS models from generating the dull samples with mean distribution. Prosody-TTS achieves high-fidelity speech synthesis with rich and diverse prosodic attributes. Experiments results demonstrate that it surpasses the state-of-the-art models in terms of audio quality and prosody naturalness. The downstream evaluation and ablation studies further demonstrate the effectiveness of each design.

## Comparison with other models

### Single-Speaker LJSpeech

<ruby>Text: the invention of movable metal letters in the middle of the fifteenth century may justly be considered as the invention of the art of printing. </ruby>

<table>
	<thead>
		<tr>
			<th style="text-align: center">GT</th>
            <th style="text-align: center">GT (voc)</th>
			<th style="text-align: center">FastSpeech 2</th>
			<th style="text-align: center">Meta-StyleSpeech</th>
            <th style="text-align: center">Glow-TTS</th>
			<th style="text-align: center">Grad-TTS</th>
			<th style="text-align: center">YourTTS</th>
            <th style="text-align: center">Prosody-TTS</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/GT/LJ001-0005.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/GT(voc)/LJ001-0005.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/FastSpeech2/LJ001-0005.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/StyleSpeech/LJ001-0005.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/GlowTTS/LJ001-0005.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/Grad-TTS/LJ001-0005.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/YourTTS/LJ001-0005.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/Prosody-TTS/LJ001-0005.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


<ruby>Text: printing, then, for our purpose, may be considered as the art of making books by means of movable types. </ruby>

<table>
	<thead>
		<tr>
			<th style="text-align: center">GT</th>
            <th style="text-align: center">GT (voc)</th>
			<th style="text-align: center">FastSpeech 2</th>
			<th style="text-align: center">Meta-StyleSpeech</th>
            <th style="text-align: center">Glow-TTS</th>
			<th style="text-align: center">Grad-TTS</th>
			<th style="text-align: center">YourTTS</th>
            <th style="text-align: center">Prosody-TTS</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/GT/LJ001-0009.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/GT(voc)/LJ001-0009.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/FastSpeech2/LJ001-0009.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/StyleSpeech/LJ001-0009.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/GlowTTS/LJ001-0009.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/Grad-TTS/LJ001-0009.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/YourTTS/LJ001-0009.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/Prosody-TTS/LJ001-0009.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


### Diverse Multi-Speaker LibriTTS
<ruby>Text: The young Englishmen were introduced to everybody, entertained by everybody, intimate with everybody.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">GT</th>
            <th style="text-align: center">GT (voc)</th>
			<th style="text-align: center">FastSpeech 2</th>
			<th style="text-align: center">Meta-StyleSpeech</th>
            <th style="text-align: center">Glow-TTS</th>
			<th style="text-align: center">Grad-TTS</th>
			<th style="text-align: center">YourTTS</th>
            <th style="text-align: center">Prosody-TTS</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/GT/003.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/GT(voc)/003.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/FastSpeech2/003.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/StyleSpeech/003.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/GlowTTS/003.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/Grad-TTS/003.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/YourTTS/003.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/Prosody-TTS/003.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: He spoke instead, in a light tone, as his pen still ran along.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">GT</th>
            <th style="text-align: center">GT (voc)</th>
			<th style="text-align: center">FastSpeech 2</th>
			<th style="text-align: center">Meta-StyleSpeech</th>
            <th style="text-align: center">Glow-TTS</th>
			<th style="text-align: center">Grad-TTS</th>
			<th style="text-align: center">YourTTS</th>
            <th style="text-align: center">Prosody-TTS</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/GT/004.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/GT(voc)/004.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/FastSpeech2/004.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/StyleSpeech/004.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/GlowTTS/004.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/Grad-TTS/004.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/YourTTS/004.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/Prosody-TTS/004.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


<ruby>Text: In a few days I had so far recovered my health that I could sit up all day, and walk out sometimes.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">GT</th>
            <th style="text-align: center">GT (voc)</th>
			<th style="text-align: center">FastSpeech 2</th>
			<th style="text-align: center">Meta-StyleSpeech</th>
            <th style="text-align: center">Glow-TTS</th>
			<th style="text-align: center">Grad-TTS</th>
			<th style="text-align: center">YourTTS</th>
            <th style="text-align: center">Prosody-TTS</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/GT/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/GT(voc)/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/FastSpeech2/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/StyleSpeech/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/GlowTTS/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/Grad-TTS/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/YourTTS/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/Prosody-TTS/002.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: There was not a worse vagabond in Shrewsbury than old Barney the piper.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">GT</th>
            <th style="text-align: center">GT (voc)</th>
			<th style="text-align: center">FastSpeech 2</th>
			<th style="text-align: center">Meta-StyleSpeech</th>
            <th style="text-align: center">Glow-TTS</th>
			<th style="text-align: center">Grad-TTS</th>
			<th style="text-align: center">YourTTS</th>
            <th style="text-align: center">Prosody-TTS</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/GT/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/GT(voc)/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/FastSpeech2/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/StyleSpeech/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/GlowTTS/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/Grad-TTS/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/YourTTS/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LibriTTS/Prosody-TTS/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


## Ablation Study
<ruby>Text: There was not a worse vagabond in Shrewsbury than old Barney the piper.</ruby>
<table>
	<thead>
		<tr>
            <th style="text-align: center">Prosody-MAE</th>
			<th style="text-align: center">w/o LDM</th>
			<th style="text-align: center">w/o VQ</th>
            <th style="text-align: center">Local Prosody</th>
			<th style="text-align: center">Variational Inference</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Ablation/Prosody-MAE/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Ablation/w_o_ldm/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Ablation/w_o_vq/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Ablation/LocalProsody/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Ablation/Variational/001.wav" type="audio/wav"></audio></td>
        </tr>
	</tbody>
</table>

<ruby>Text: In a few days I had so far recovered my health that I could sit up all day, and walk out sometimes.</ruby>
<table>
	<thead>
		<tr>
            <th style="text-align: center">Prosody-MAE</th>
			<th style="text-align: center">w/o LDM</th>
			<th style="text-align: center">w/o VQ</th>
            <th style="text-align: center">Local Prosody</th>
			<th style="text-align: center">Variational Inference</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Ablation/Prosody-MAE/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Ablation/w_o_ldm/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Ablation/w_o_vq/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Ablation/LocalProsody/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Ablation/Variational/002.wav" type="audio/wav"></audio></td>
        </tr>
	</tbody>
</table>



## Generalization To Unseen Data (VCTK)
<ruby>Text: We also need a small plastic snake and a big toy frog for the kids.</ruby>
<table>
	<thead>
		<tr>
            <th style="text-align: center">GT</th>
			<th style="text-align: center">GT(voc.)</th>
			<th style="text-align: center">Prosody-TTS</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/VCTK_OOD/GT/p225_004.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/VCTK_OOD/GT_voc/p225_004.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/VCTK_OOD/Prosody-TTS/p225_004.wav" type="audio/wav"></audio></td>
        </tr>
	</tbody>
</table>

<ruby>Text: Six spoons of fresh snow peas, five thick slabs of blue cheese, and maybe a snack for her brother Bob.</ruby>
<table>
	<thead>
		<tr>
            <th style="text-align: center">GT</th>
			<th style="text-align: center">GT(voc.)</th>
			<th style="text-align: center">Prosody-TTS</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/VCTK_OOD/GT/p226_003.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/VCTK_OOD/GT_voc/p226_003.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/VCTK_OOD/Prosody-TTS/p226_003.wav" type="audio/wav"></audio></td>
        </tr>
	</tbody>
</table>




## GT Duration Comparison
<ruby>Text: has never been surpassed.</ruby>
<table>
	<thead>
		<tr>
            <th style="text-align: center">Backbone(FastSpeech 2)</th>
			<th style="text-align: center">Backbone(FastSpeech 2) + GT Duration</th>
			<th style="text-align: center">Prosody-TTS</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/FastSpeech2/LJ001-0008.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/FastSpeech2_gtdur/LJ001-0008.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/Prosody-TTS/LJ001-0008.wav" type="audio/wav"></audio></td>
        </tr>
	</tbody>
</table>

<ruby>Text: that the forms of printed letters should follow more or less closely those of the written character, and they followed them very closely.</ruby>
<table>
	<thead>
		<tr>
            <th style="text-align: center">Backbone(FastSpeech 2)</th>
			<th style="text-align: center">Backbone(FastSpeech 2) + GT Duration</th>
			<th style="text-align: center">Prosody-TTS</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/FastSpeech2/LJ001-0017.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/FastSpeech2_gtdur/LJ001-0017.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/LJSpeech/Prosody-TTS/LJ001-0017.wav" type="audio/wav"></audio></td>
        </tr>
	</tbody>
</table>
