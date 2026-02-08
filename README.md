# Forced Alignment using Montreal Forced Aligner (MFA)

## 📌 Objective

The goal of this assignment is to build a complete forced alignment
pipeline using the **Montreal Forced Aligner (MFA)** tool and understand
how speech audio aligns with phonetic transcriptions at the word and
phoneme levels.

------------------------------------------------------------------------

## 🔹 What is Forced Alignment?

Forced alignment is the process of synchronizing audio recordings with
their corresponding transcripts to determine when each word and phoneme
occurs in the speech signal.

This is widely used in:

-   Speech recognition\
-   Text-to-speech systems\
-   Linguistic research\
-   Subtitle generation

------------------------------------------------------------------------

## 🛠️ Environment Setup

### Step 1: Install Conda (Recommended)

Download Miniconda or Anaconda.

### Step 2: Create MFA Environment

``` bash
conda create -n mfa python=3.8
conda activate mfa
```

### Step 3: Install Montreal Forced Aligner

``` bash
pip install montreal-forced-aligner
```

Verify installation:

``` bash
mfa version
```

------------------------------------------------------------------------

## 📂 Dataset Preparation

Organize files in the MFA-required format:

    dataset/
     ├── wav/
     │    ├── audio1.wav
     │    ├── audio2.wav
     │
     ├── transcripts/
          ├── audio1.txt
          ├── audio2.txt

Ensure:

✅ File names match exactly\
✅ Transcripts are in uppercase\
✅ No punctuation

Example transcript:

    HELLO WORLD

------------------------------------------------------------------------

## 📖 Dictionary Selection

For this project, the pretrained MFA dictionary was used:

    english_us_arpa

Download:

``` bash
mfa model download dictionary english_us_arpa
mfa model download acoustic english_us_arpa
```

------------------------------------------------------------------------

## ▶️ Running Forced Alignment

``` bash
mfa align dataset english_us_arpa english_us_arpa output_folder
```

After execution, **TextGrid files** are generated inside the output
folder.

------------------------------------------------------------------------

## 🔍 Inspecting Results

Open TextGrid files using **Praat**.

Observe:

-   Word boundaries\
-   Phoneme segmentation\
-   Timing precision

------------------------------------------------------------------------

## ⚠️ Handling Out-of-Vocabulary (OOV) Words

OOV words occur when a transcript contains words not present in the
dictionary.

### Detect OOV Words:

``` bash
mfa validate dataset english_us_arpa
```

### Solution: Use G2P Model

Generate pronunciations automatically:

``` bash
mfa model download g2p english_us_arpa
mfa g2p english_us_arpa transcripts/ generated_dict.txt
```

Then rerun alignment using the updated dictionary.

------------------------------------------------------------------------

## ✅ Outputs

-   TextGrid alignment files\
-   Updated pronunciation dictionary\
-   Alignment logs

------------------------------------------------------------------------

## 🚀 How to Run This Project

1.  Install MFA\
2.  Prepare dataset\
3.  Download dictionary + acoustic model\
4.  Run alignment\
5.  Handle OOV words\
6.  Inspect results in Praat

------------------------------------------------------------------------

## 📊 Key Learnings

-   MFA provides highly accurate phoneme-level alignment.
-   Dictionary coverage significantly impacts alignment quality.
-   OOV handling improves timing precision.
