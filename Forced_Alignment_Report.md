# Forced Alignment Report

## 1. Introduction

This project implements a forced alignment pipeline using the Montreal
Forced Aligner (MFA) to synchronize speech audio with textual
transcripts at both word and phoneme levels.

------------------------------------------------------------------------

## 2. Model and Dictionary Used

-   **Acoustic Model:** english_us_arpa\
-   **Pronunciation Dictionary:** english_us_arpa pretrained dictionary

The pretrained models were selected because they are optimized for
English speech and provide reliable phonetic mappings.

------------------------------------------------------------------------

## 3. Alignment Process

The dataset containing `.wav` audio files and matching transcripts was
organized according to MFA requirements. Forced alignment was executed
using the pretrained acoustic model and dictionary.

The aligner generated **TextGrid files**, which include:

-   Word-level timestamps\
-   Phoneme boundaries\
-   Silence detection

------------------------------------------------------------------------

## 4. Sample Alignment Observations

### Word Alignment

Most words were accurately segmented with minimal timing offsets.

### Phoneme Alignment

Phoneme boundaries closely matched speech patterns, demonstrating the
effectiveness of Hidden Markov Model-based acoustic alignment.

------------------------------------------------------------------------

## 5. Errors Observed Before OOV Handling

Some alignment issues were detected:

-   Skipped phonemes\
-   Slight boundary shifts\
-   Misalignment for rare words

The root cause was missing pronunciations in the dictionary.

------------------------------------------------------------------------

## 6. Handling Out-of-Vocabulary (OOV) Words

OOV words were identified using MFA validation tools.

A **Grapheme-to-Phoneme (G2P)** model was used to generate
pronunciations automatically.

### Result After OOV Handling:

-   Improved phoneme segmentation\
-   Reduced alignment errors\
-   Better timing accuracy

------------------------------------------------------------------------

## 7. Key Insights

-   Dictionary completeness is critical for accurate alignment.
-   Pretrained MFA models provide strong baseline performance.
-   Automatic pronunciation generation significantly improves results.

------------------------------------------------------------------------

## 8. Conclusion

The forced alignment pipeline was successfully implemented using
Montreal Forced Aligner. The experiment demonstrated how acoustic models
and pronunciation dictionaries work together to produce precise
speech-text synchronization.

Handling OOV words further enhanced alignment quality, making the system
robust for real-world speech datasets.
