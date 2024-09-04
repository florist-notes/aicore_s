## MLPerf Training Benchmark

ML Perf Training Benchmark [[paper](https://arxiv.org/abs/1910.01500)] - paper : ["MLPERF TRAINING BENCHMARK
"](https://par.nsf.gov/servlets/purl/10197595) )

<p align="justify">
MLPerf is a benchmark suite that is used to evaluate training and inference performance of on-premises and cloud platforms. MLPerf is intended as an independent, objective performance yardstick for software frameworks, hardware platforms, and cloud platforms for machine learning. A consortium of AI community researchers and developers from more than 30 organizations developed and continue to evolve these benchmarks. The goal of MLPerf is to give developers a way to evaluate hardware architectures and the wide range of advancing machine learning frameworks.
</p>

+ `Benchmark Categories`: MLPerf Training Benchmarks cover a variety of machine learning tasks that represent common and critical workloads in the field. These tasks are selected to provide a comprehensive evaluation of system performance across different domains, including:

    + `Image Classification`: Benchmarks like ResNet-50 measure how fast a system can train models on large image datasets (e.g., ImageNet).
    + `Object Detection`: Models like SSD (Single Shot Multibox Detector) and Mask R-CNN are used to assess the performance of systems on object detection tasks.
    + `Natural Language Processing (NLP)`: Benchmarks include tasks like BERT (Bidirectional Encoder Representations from Transformers) for language understanding and translation.
    + `Reinforcement Learning`: Tasks such as MiniGo, based on the game of Go, are used to evaluate reinforcement learning performance.
    + `Recommendation Systems`: The Deep Learning Recommendation Model (DLRM) benchmark measures performance on tasks related to recommendation engines, common in industry applications.
    + `Speech Recognition`: The RNN-T (Recurrent Neural Network Transducer) benchmark tests systems on speech-to-text tasks.

MLPerf Submission Categories:

<table width=100%>
<tr>

<td>
Image Classification
<img src="dog.svg" width=100%>
</td>

<td>
Object Detection (Lightweight)
<img src="objd.svg" width=100%></td>

<td>
Object Detection (Heavyweight)
<img src="objdh.svg" width=100%>
</td>
<td>

Biomedical Image Segmentation
<img src="bio.svg" width=100%>
</td>

</tr>




<tr>

<td>
Automatic Speech Recognition (ASR)
<img src="asr.svg" width=100%>
</td>

<td>
Natural Language Processing (NLP)
<img src="nlp.svg" width=100%></td>

<td>
Recommendation
<img src="rr.svg" width=100%>
</td>
<td>

Large Language Model (GPT-3 175B)
<img src="llm.svg" width=100%>
</td>

</tr>



<tr>

<td>
Climate Atmospheric River Identification
<img src="cl.svg" width=100%>
</td>

<td>
Cosmology Parameter Prediction
<img src="cos.svg" width=100%></td>

<td>
Quantum Molecular Modeling
<img src="mol.svg" width=100%>
</td>

</tr>


</table>


results - [training v2.1](https://mlcommons.org/en/training-normal-21/) | [code](https://github.com/mlcommons/training), [NVIDIA MLPerf Benchmarks](https://www.nvidia.com/en-us/data-center/resources/mlperf-benchmarks/) | [Demystifying the MLPerf Training Benchmark Suite](https://ieeexplore.ieee.org/document/9238612) 🌸