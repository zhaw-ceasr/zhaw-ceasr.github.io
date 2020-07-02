---
layout: single
title: "CEASR Corpus Structure"
permalink: /corpus-structure/
header:
  image: /assets/images/audio_wave_bw.jpg
---

CEASR contains two data sets:
* English (``CEASR_en``)
* and German (``CEASR_de``),

both containing a set of JSON files.

**One JSON data file** comprises utterances from **one speech corpus** transcribed by **one ASR system** in a particular configuration.

The name of the JSON file contains both the system name (or alternatively ID, in case we cannot reveal the system's name)
and the corpus name, which are separated with 2 underscores, e.g. ``D2__librispeech_other.json``
(when the system name cannot be disclosed) or ``kaldi_librispeech__commonvoice.json``.

For more information on the JSON files go to [JSON Data File Structure](https://ceasr-corpus.github.io/data-structure/).