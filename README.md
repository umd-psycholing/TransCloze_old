# Overview

This pipline facilitates automatic processing of auditory data, especially the cloze data, where:

1. responses are open ended
2. responses are typically short (mostly a single word)
3. latency of the production is valuable data

However, it could be used for processing of other kinds of data.

![overview](/Users/masato/Documents/Research/pipeline_prep/overview.png)

Roughly speaking, this pipleline 

1. takes webm files with responses from PCIbex 
2. transforms it into wav files (wav2webm)

3. gets onset data from Chronset (citation)

4. gets automatic transcription from Google Cloud Speech-to-Text API (documentation)

5. combines the information + context/probe info of the experiment



Output: 

1. csv files mapping audio file names onto transcription and onset
2. TextGrid files with automatic transcription + onset, which could be used for correction in Praat



- Get onset data from Chronset
- Get trasncription from Google Cloud Speech-to-Text API



# Preperation

## Data

- A directory containing webm files



File names must end with: \[item_condition\]\[condition\]_\[participant_id\] (e.g. exp_10a_tdlf.webm)



## Environment

Requirements:

Core:

python ver

numpy

pandas

pickle

pydub

- 



This pipeline is built for OSX. Might need some modification for Windows and LINUX.



# webm2wav

### What this file does:

The output audio files of PCIbex are usually separated by participants, but it is not straightforward to convert files in different folders. (It is tedious to convert the webm files into wav files for each of the 100 participants.) The "webm2wav" file recursively convert all the webm wiles below a certain directory at once.



### What you need:

- ffmpeg
- a bash script named "webm2wav"



### What to do:

Enter the following line into your command line.

```bash
bash location_of_webm2wav input_file_directory output_file_directory
```

- First argument:  the path to "webm2wav" file
- Second argument: the path to the directory which contaions all the webm files
- Third argument: the path to the output directory

NOTE: All the wav files below the input directry will be generated directly in the output directory



# transcribe.ipynb

This script generates NLP-powered transcriptions of audio files and ouput TextGrid files with transcriptions. See transcribe.ipynb for details







# CheckAndEdit

This Praat script:

1. open TextGrid and wav files with the same name and present them together
2. saves edits on the TextGrid



Simply enter the path to the wav files and textgrids to the box, and then the corresponding files are opened at once.



Be careful that the script overwrites the TextGrid file once you click on "continue"









