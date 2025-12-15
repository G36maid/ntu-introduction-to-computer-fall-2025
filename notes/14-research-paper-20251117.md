# Sync Lip Movements to Dubbing Audio (配音口型同步)

**Presenter:** 羅翡瑩 Valencia Lo
**Email:** vlooo.sch@gmail.com
**Date:** 2025-11-17

---

## 1. Introduction

### Problem Statement
*   Traditional dubbing only changes the audio without adjusting lip movements.
*   "Have you ever watched a movie where the actor’s lips don’t match the words you hear? It feels strange, right?"
*   It is difficult to identify who is talking if lips don't move accordingly.
*   Manual fixing is time-consuming and expensive.

### Project Objectives
*   Develop a system for the film industry to synchronize lip movements with dubbed speech.
*   Implement **speaker identification** to recognize and sync multiple people's lips accurately.
*   Optimize the system to process longer videos.

---

## 2. Methodology

### Wav2Lip
*   **Function**: A model designed to synchronize lip movements in videos with corresponding audio.
*   **Cons**:
    *   Only supports single speaker; cannot identify *which* speaker needs changes.
    *   If no face is present, random mouth shapes may appear.
    *   Works best for video quality lower than 720p.
    *   Struggles with side-face angles.

### Face Recognition
*   **Purpose**: Ensure that Wav2Lip is applied to the correct speaker's face.
*   **Process**: Replaces batch-face processing with face recognition combined with Euclidean distance calculation. Matches facial coordinates with the assigned text script/speaker ID.

### Faster-Whisper
*   **Function**: Reimplementation of OpenAI's Whisper model (faster). Used for speech-to-text conversion and timestamp generation.
*   **Pros**: Fast, handles multiple languages effectively.
*   **Cons**: Does not support speaker diarization (cannot distinguish *who* is speaking).

### NeMo 2.0 (NVIDIA Neural Modules)
*   **Function**: Provides ASR (Automatic Speech Recognition) and TTS (Text To Speech).
*   **Key Feature**: **Speaker Diarization** – identifies and labels different speakers based on distinct voices.
*   **Cons**: Requires more customization effort and is slower than Faster-Whisper.

---

## 3. Implementation Workflow

### Interface Steps
1.  **Input**: Upload video file, dubbed audio file, and actor images.
2.  **Process**:
    *   Use **Faster-Whisper + NeMo** to transcribe audio to text, label speakers (Speaker Diarization), and generate timestamps.
    *   **Edit Script**: User reviews generated script.
    *   **Assign**: User assigns actor images to the identified speaker IDs.
3.  **Core Processing**:
    *   Cut video into clips based on timestamps.
    *   **Speaker Identification**: Match clips to actor images.
    *   **Face Recognition**: Locate target actor's face in the clip.
    *   **Wav2Lip**: Adjust only the speaking actor's mouth shape.
    *   **Combine**: Merge all lip-synced clips.
4.  **Output**: Final lip-synced video.

---

## 4. Results

*   **Speech Recognition**: Generates transcriptions quickly and accurately labels speakers. Allows manual adjustment if needed.
*   **Lip Synchronization**:
    *   Face recognition achieves **>80% accuracy**.
    *   Successfully matches lips with dubbed speech.
    *   **Limitation**: Mouth movements may have slight artifacts depending on video quality.
*   **Impact**: Proves practicability for multi-language and multi-character dubbing scenarios.

---

## 5. Conclusion and Future Work

### Conclusion
The system successfully achieves multilingual lip synchronization in multi-character scenes by integrating Faster-Whisper, NeMo, and Wav2Lip. It overcomes traditional limitations by maintaining audio-visual synchronization even during frequent character switches.

### Future Improvements
1.  **Performance**: Improve processing speed and resource utilization efficiency.
2.  **Quality**: Support higher resolution video and reduce blurring in the resulting lip shapes.

---

## 6. Summary Steps
1.  **Acquire Data**: Video, Audio, Actor Images.
2.  **Speech Recognition**: Transcribe & Diarize (Whisper + NeMo).
3.  **Identify**: Match Audio segments to Actors.
4.  **Sync**: Apply Wav2Lip to specific faces.
5.  **Merge**: Recombine clips into final video.