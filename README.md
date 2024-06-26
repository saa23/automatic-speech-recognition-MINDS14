# automatic-speech-recognition-MINDS14

# 1. Introduction
Automatic Speech Recognition (ASR) is technique in NLP that focuses specifically on converting **speech to text**. That means the machine is able to convert any input type audio dataset into output text.

Some application related to ASR as follows:
- improve accessibility(enable person with dissabilities to access spoken context)
- virtual assistant (such as Siri, Google Assistant, or Amazon Alexa)
- Language learning (providing feed-back on pronunciation and language practice)
- and many more...

The project uses *MINDS-14 dataset* which popular in domain research. Specifically uses the *en-US* language version dataset.

As for the models, we use fine-tune some pre-trained models: **WAV2VEC2, Whisper, and HuBERT**.

# 2. Objectives
1. Develop AI models for ASR task by using pre-trained models: WAV2VEC2, Whisper, and HuBERT
2. fine-tuning those pre-trained models until get a good model performance

# 3. Dataset
The project uses the [MINDS-14 dataset](https://huggingface.co/datasets/PolyAI/minds14).

Paper on detailed information on MINDS-14 dataset entitled *"Multilingual and Cross-Lingual Intent Detection from Spoken Data"*.

The dataset itself contains audio data with versions in **14 languages and 14 classes of intentions** taken from commercial system in the e-banking domain.

While the data structure as below:
- path (str)
- audio (dict)
    - path (str)
    - array (array)
    - sampling_rate (int)
- transcription (str)
- english_transcription (str)
- intent_class (int)
- lang_id (int)

# 4. Project Flow

![Flow Diagram](./images/flow-diagram.png)

1. Explore the data to get some general insights related to the dataset used (practicing EDA).
    1. Distribution of speech length per class
    <br/>   
    <img src="./images/length-by-class.png" alt="distribution length by class" width="500"/>
    <br/>

    2. waveform
    <br/>
    <img src="./images/waveform.png" alt="waveform" height="150"/>
    <br/>

    3. spectogram
    <br/>
    <img src="./images/spectogram.png" alt="spectogram" height="150"/>
    <br/>

    4. MFCC (Mel Frequency Cepstral Coefficients)
    <br/>
    <img src="./images/mfcc.png" alt="mfcc" height="150"/>
    <br/>

    5. FFT (Fast Fourier Transform)
    <br/>
    <img src="./images/fft.png" alt="fft" height="150"/>
    <br/>

2. Experimentation using pre-trained models: WAV2VEC2-base, Whisper-tiny, and HuBERT-large.
3. The models are fine-tuned with the MINDS-14 dataset, specifically using the en-US (US English) language version.
4. The pre-process and training stages are more or less as follows:
    1. Convert input data transcription to uppercase
    2. Split data into train and test sets (80:20 respectively)
    3. Set processor (to pre-processing audio dataset into data vector format)
    4. Generate Data Collator object
    5. Load pre-trained model 
    6. Define training args
    7. Define object *Trainer*
    8. Fine-tune model using *Trainer*  with metric evaluation WER (Word Error Rate).
5. Execute inference prediction with fine-tuned
6. Evaluate the models using WER and CER.


# 5. Output

- Some outputs give very good results
<br/>
<img src="./images/output1-good.png" alt="good results"/>
<br/>
<br/>
<img src="./images/output2-pretty-good.png" alt="pretty good results"/>
<br/>

- But for other cases still need improvements
<br/>
<img src="./images/output3-no-good.png" alt="no good"/>
<br/>