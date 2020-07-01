---
layout: single
title: "JSON Data File Structure"
permalink: /data-structure/
header:
  image: /assets/images/audio_wave_bw.jpg
---

Each JSON data file contains three objects: ``corpus``, ``system`` and ``dataset``.

### ``corpus``
``corpus`` provides basic corpus information:

```
{"corpus": {
    "identifier": String,
    "license": String,
    "documentation_link": String,
    "download_link": String,
    "cost": Boolean,
    "incomplete_utterances_removed_%": Float,
    "missing_corpus_data": Dictionary,
    "original_reference_segmentation": String,
    "original_audio_segmentation": String
}
```

### ``system``
``system`` contains identifier (either the system full configuration or its ID)
as well as the information on the model and language code that were applied
for the particular transcription:

```
"system": {
    "identifier": String,
    "model": String,
    "language_code": String
}
```

### ``dataset``
``dataset`` provides detailed information about the utterance set including metadata
and basic statistics as well as the ``utterances`` list itself:

```
"dataset": {
    "language": String,
    "speaking_style": String,
    "num_utterances": Integer,
    "total_duration": Float,
    "average_audio_duration": Float,
    "num_speaker_noise_references": Integer,
    "%_overlapping_utterances": Float,
    "max_num_overlapping_utterances": Integer,
    "num_utterances_containing_non_lexical_sounds": Integer,
    "num_utterances_containing_only_non_lexical_sounds": Integer,
    "average_speaking_rate": Float,
    "recording_devices": String,
    "acoustic_environments": String,
    "overlapping_speech": String,
    "utterances_per_gender": Dictionary,
    "utterances_per_dialect": Dictionary,
    "utterances_per_accent": Dictionary,
    "num_speakers": Integer,
    "max_num_utterances_per_speaker": Integer,
    "min_num_utterances_per_speaker": Integer,
    "avg_num_utterances_per_speaker": Float,
    "utterances": List
}
```


