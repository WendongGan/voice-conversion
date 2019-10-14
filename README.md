# voice-conversion

**The code is coming soon**

blog website: [zeroqiaoba.github.io/voice-conversion](https://zeroqiaoba.github.io/voice-conversion/)

## PPGs-based Voice Conversion

Phonetic PosteriorGrams (PPGs) has been successfully applied to non-parallel VC. The PPG is a sequence of frame-level linguistic information representation obtained from the speaker-independent automatic speech recognition system. The PPGs-based VC frameworks mainly consist of two key components: the conversion model and vocoder.  The conversion model converts PPGs extracted from the source speech into acoustic features of the target speaker.  Then the vocoder uses these converted features to synthesize the speech waveform of the target speaker.          



## Baseline System

Vocoders influence the quality of converted speech. Prior works utilize conventional parametric vocoders for VC (such as STRAIGHT and WORLD).   However, these vocoders limit the speech quality. To address this issue, researches focus on the WaveNet vocoder. The WaveNet vocoder can directly estimate the time domain waveform samples conditioned on input features.  It is shown to improve the generated speech quality significantly. However, the WaveNet vocoder runs slower than the real time. Recently, an efficient neural vocoder called LPCNet is proposed. This vocoder can synthesize speech with close to natural quality while running faster than real time on a standard CPU. Therefore, we use the LPCNet vocoder for VC. To control the prosody of the generated speech, we use the pitch and the vuv features as additional inputs. 



 ![1](https://github.com/zeroQiaoba/voice-conversion/raw/master/image/1.png)



## Proposed Method

Despite the good performance of the baseline system, it still has some limitations. Firstly, the pitch detection algorithms face challenges in noise and singing conditions. Secondly, the prosody is related with many factors, including the intonation, stress, rhythm and pitch. In the baseline system, we only utilize the pitch to control the prosody of the generated speech. We find this system performs badly on some challenging situations, such as the source speech is a singing voice.

To overcome the above limitations, we utilize the reference encoder to learn a latent prosody  representation from the input speech directly. We introduce temporal structures in the reference encoder,             thus enabling fine-grained control of the prosody of the converted speech. 

 ![1](https://github.com/zeroQiaoba/voice-conversion/raw/master/image/2.png)
