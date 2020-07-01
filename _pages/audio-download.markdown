---
layout: single
title: "Audio Recordings Download"
permalink: /audio-download/
header:
  image: /assets/images/audio_wave_bw.jpg
---

The CEASR data set provides transcripts of audio recordings but does not provide the recordings themselves.

In order to get access to the audio files, the corresponsing speech corpora mentioned under [CEASR Scope]() needs to be downloaded or purchased separately.
All English and three of the German corpora included in CEASR are available for download without any costs.
The remaining three German corpora must be purchased.
The information on the corpus availability as well as the download links
or links to speech resources catalogues are provided within the ``corpus`` object of each JSON file. An example for the CommonVoice corpus:

```
{"corpus": {
    "identifier": "commonvoice_de",
    "license": "https://www.mozilla.org/en-US/foundation/licensing/website-content/",
    "documentation_link": "https://voice.mozilla.org/de",
    "download_link": "https://voice.mozilla.org/de/datasets",
    "incomplete_utterances_removed_%": 0.0,
    "missing_corpus_data": {
        "missing_speaker_id": 5633,
        "missing_dialect": 4927,
        "missing_accent": 4874,
        "missing_gender": 4680},
    "original_reference_segmentation": "multiple_words",
    "original_audio_segmentation": "multiple_words",
    "free_of_charge": true}
```

After downloading a speech corpus, you can retrieve the names of the audio files corresponding to each utterance from the JSON data file.

Open a JSON data file which contains transcripts of this corpus,
e.g. after downloading CommonVoice go to CEASR to the JSON file ``kaldi_aspire__commonvoice.json``
(or any other file ending with ``__commonvoice.json``).

In ``kaldi_aspire__commonvoice.json``, go to the ``utterances`` list in the ``dataset`` object. For each utterance in the list, the ``audio_file_path`` is provided in the utterance ``audio`` object, e.g.:
```
"audio": {
    "audio_file_path": "/commonvoice/cv_corpus_v1/cv-valid-test/sample-000000.mp3",
    "duration": 3.192,
    "samplerate": 8000,
    "bitdepth": 16,
    "channels": 1,
    "encoding": "Signed Integer PCM",
    "num_samples": 25536},
```
This is the path to the original audio file as provided by the corpus.

If the corpus contains unsegmented audio recordings, as it is the case for example for the AMI corpus
(the audio files contain recordings of the whole meetings),
you need to trim the audios according to the ``start time`` and ``end time`` provided in the ``reference`` object of the utterance.
The path to the original unsegmented audio file is provided also in the ``audio`` object as ``audio_file_path``. E.g.:

```
"reference": {
    "text": "last",
    "original_text": "Last .",
    "only_non_lexical_sounds": false,
    "start_time": 142.832,
    "end_time": 144.896},
"audio": {
    "audio_file_path": "/ami/amicorpus/IS1000a/audio/IS1000a.Headset-2.wav",
    "duration": 2.064,
    "samplerate": 8000,
    "bitdepth": 16,
    "channels": 1,
    "encoding": "Signed Integer PCM",
    "num_samples": 16512}
```