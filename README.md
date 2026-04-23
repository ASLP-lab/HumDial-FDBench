# Full-Duplex Interaction in Spoken Dialogue Systems: A Comprehensive Study from the ICASSP 2026 HumDial Challenge

This repository publicly releases the **HumDial-FDBench dataset** and the **HumDial-FDBench**. The dataset is built from dual-channel real human-recorded conversations and captures realistic conversational phenomena such as interruptions, overlapping speech, and dynamic turn negotiation. Based on this dataset, HumDial-FDBench is designed to evaluate a system’s ability to handle interruptions and maintain conversational continuity during concurrent listening and generation.

In addition to the dataset, we provide a public leaderboard reporting results from challenge submissions, open-source models, and proprietary systems under a unified evaluation protocol. Together, these resources provide a shared benchmark for studying full-duplex spoken dialogue interaction and support future research toward more responsive and human-like conversational systems.

## Dataset

### Download

The train, develop, and test sets can be downloaded from [HumDial-FDBench](https://huggingface.co/datasets/ASLP-lab/HumDial-FDBench)

### Scenarios

The released dataset covers two major scenario categories: **Interruption** and **Rejection**, comprising **nine sub-scenarios** in total.

The Interruption category evaluates whether a system can appropriately adapt its ongoing response when the user intervenes. It includes the following five scenarios:

- **Follow-up Question**: the user interrupts to ask a related question and expects an immediate and relevant response.
- **Negation or Dissatisfaction**: the user expresses disagreement, correction, or dissatisfaction during the system response, requiring the system to promptly adjust its output.
- **Repetition Request**: the user asks the system to repeat what was said, usually because of inaudibility or misunderstanding.
- **Topic Switch**: the user abruptly shifts to a new topic, requiring the system to transition smoothly and coherently.
- **Silence or Stop**: the user explicitly asks the system to stop speaking, and the system is expected to cease output immediately while remaining ready to resume later.

The Rejection category evaluates whether a system can correctly withhold responses to non-actionable, irrelevant, or misdirected speech. It includes the following four scenarios:

- **User Real-time Backchannels**: short acknowledgments such as “uh-huh” or “yeah” that should not interrupt the system’s ongoing response.
- **Pause Handling**: hesitations or pauses within the user’s utterance, where the system should wait until the user’s intent is fully expressed.
- **Third-party Speech**: background speakers who interject before or after the target user query; the system should ignore these utterances.
- **Speech Directed to Others**: cases where the user temporarily addresses another person, often on an unrelated topic, and the system is expected to detect and ignore such speech.

The table below shows the number of instances in each split.

| Category | Scenario | Train | Dev | Test |
|---|---|---:|---:|---:|
| Interruption | Follow-up Question | 1507 | 200 | 600 |
| Interruption | Negation or Dissatisfaction | 1211 | 200 | 600 |
| Interruption | Repetition Request | 1213 | 200 | 600 |
| Interruption | Topic Switch | 1213 | 200 | 600 |
| Interruption | Silence or Stop | 1212 | 200 | 600 |
| Rejection | User Real-time Backchannels | 1211 | 200 | 600 |
| Rejection | Pause Handling | 1211 | 200 | 600 |
| Rejection | Third-party Speech | 120 | 200 | 600 |
| Rejection | Speech Directed to Others | 0 | 200 | 200 |
## HumDial-FDBench Benchmark

Based on the released conversational data, we construct **HumDial-FDBench**, a benchmark for evaluating full-duplex spoken dialogue systems.
The HumDial-FDBench evaluation protocol is built upon Full-Duplex-Bench v1.5 and introduces several extensions to support more complex interaction scenarios and a more comprehensive assessment of full-duplex dialogue systems.

HumDial-FDBench focuses on a system’s ability to:

- detect and respond to interruptions,
- manage speech overlap,
- maintain conversational continuity,
- and preserve natural interaction flow.

The benchmark is intended to provide a more realistic evaluation setting than traditional turn-based dialogue benchmarks.

### Public Leaderboard

To encourage transparent and reproducible evaluation, we provide a public leaderboard for benchmarking both open-source and proprietary systems.
**D-Sco.** denotes **Delay Score**, which measures the system's performance on delay-related metrics.  
`*` indicates a late submission.

| Team | Int. | Rej. | Delay (s) | D-Sco. | Final | Rank |
|---|---:|---:|---:|---:|---:|---:|
| Cookie asr | 79.3 | 72.2 | 1.260 | 79.9 | 76.6 | 1 |
| Badcat | 89.7 | 57.8 | 1.632 | 72.6 | 73.5 | 2 |
| SenseDialog | 76.4 | 60.9 | 1.237 | 80.5 | 71.0 | 3 |
| Gemini-2.5 | 79.8 | 36.5 | 1.301 | 79.0 | 62.3 | -- |
| Unity Squad* | 68.5 | 51.2 | 1.876 | 68.6 | 61.6 | -- |
| RhythmSense | 77.4 | 38.6 | 1.577 | 73.5 | 61.1 | 4 |
| Lingcon Insight | 67.6 | 38.9 | 1.127 | 83.1 | 59.2 | 5 |
| Baseline | 75.9 | 35.2 | 2.531 | 60.0 | 56.4 | 6 |
| HelloWorld | 51.3 | 36.3 | 0.624 | 100.0 | 55.0 | 7 |
| Freeze-Omni | 29.6 | 50.2 | 2.578 | 59.5 | 43.8 | -- |
| AISpeech | 47.7 | 33.9 | 3.391 | 51.6 | 43.0 | 8 |
| Cascade | 28.1 | 30.9 | 1.739 | 70.7 | 37.7 | 9 |
| Moshi | 35.4 | 22.8 | 2.876 | 56.3 | 34.5 | -- |
