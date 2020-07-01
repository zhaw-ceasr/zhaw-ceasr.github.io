---
layout: single
title: "Data Set Generation Process"
permalink: /generation/
header:
  image: /assets/images/audio_wave_bw.jpg
---

The process for generating CEASR comprised 3 steps:
1. speech corpora pre-processing
2. transcribing the utterances with ASR systems
3. transcript post-processing.

## Speech Corpora Pre-Processing

### Corpus Data Extraction
First we retrieved the audio recordings, manual transcripts (reference texts)
and metadata from the corpus. We performed a quality check in order to identify
incomplete utterances: if the original reference text or
the audio file were missing, or if the utterance start time
was after or equal to the utterance end time, we removed
the utterance from the data set. This step was necessary to
ensure all data required for generating a transcription and
aligning it with its reference was available. In total, we removed
549 utterances from the German corpora.

### Metadata Normalisation
Next, we normalised the metadata items such as gender, dialect, and mother
tongue in order to allow cross-corpus filtering and comparison
of utterances. For dialect and mother tongue, the
original data was mapped to the ISO 639-1 standard language
codes with country codes (e.g. en-US, de-AT, etc.);
for gender, all entries were normalised to ’male’ and ’female’.

### Uniform Utterance Data Structure Generation
Finally, we transformed each corpus utterance into a uniform
utterance data structure needed for further processing.

### Reference Segmentation
If the references
were provided in one large file containing multiple
annotated utterances, we retrieved each single utterance and
stored it separately according to the annotation. We aimed
at keeping the utterance lengths consistent and not exceeding
ten seconds by segmenting longer utterances. However,
we could perform this segmentation only for utterances
provided with time stamps. If no time stamps were
available, the utterances were left as provided in the original
corpus.

### Reference Normalisation
Furthermore, we removed all meta-tags from the reference
text. These are tags describing speaker noise (e.g. laughing
or coughing), non-speaker noise (e.g. rustle, squeak), or
speaker disfluencies (e.g. speaker restarts, partial words,
mispronounced words, unintelligible speech). Next to the
cleaned reference, the original reference text including the
meta-tags was stored as part of the unified utterance data as
well.
In order to reliably compare performance between different
systems, the formatting of the references and the hypotheses
must be as similar as possible. To this end, we removed
punctuation, transformed all strings to lower-case, spelled
out numbers (”forty-two” instead of ”42”), and applied consistent
formatting of integers, decimal values and time of
day.

### Audio Segmentation
In order to prepare the audio recordings for
transcription, we performed two steps: extracting audio information as well as
converting and trimming the audio file where
necessary.
Some speech corpora provide a set of audios of several
seconds, each containing one short utterance, while others
have long audios with long utterances of several minutes,
or long audios containing multiple short utterances.
When timestamps were available, we segmented all recordings
into audios of duration less than 10 seconds in order to
ensure consistency between reference text and audio segmentation.

### Audio Conversion
In the next step, we
converted the audios into the required audio formats. We
also changed the sampling rate and the bit depth according
to the requirements by the particular system. Converted audios
were then passed through to the transcription step and
the utterance data object was extended with new information
such as format, duration, sampling rate, bit depth and
number of channels of both the original audio file as well
as the converted recording.

## Corpora Transcription

The transcriptions were performed
in batches: a full set of pre-processed utterances
from one corpus was sent to an ASR system for transcribing.
Each utterance data object was enriched with the original
hypothesis text and moved to the next step, which was
hypothesis post-processing.

## Transcripts Post-Processing

In order to ensure consistency
between reference and hypothesis, we performed all reference normalisation steps
also on the hypothesis.
We tried to discover and eliminate as many discrepancies
between references and hypothesis as possible; however,
a complete consistency between the texts in terms of
formatting cannot be guaranteed.

