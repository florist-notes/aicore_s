
# AI-Benchmark Alpha

AI Benchmark Alpha is an open source python library for evaluating AI performance of various hardware platforms, including CPUs, GPUs and TPUs. The benchmark is relying on TensorFlow machine learning library, and is providing a precise and lightweight solution for assessing inference and training speed for key Deep Learning models.

web : [ai-benchmark alpha](https://ai-benchmark.com/alpha)



## CPU training:
<img src="alphacpu.png" width=100%>

## GPU training:

After successful setup of CUDA and cuDNN, import the following in python:

```python
from ai_benchmark import AIBenchmark

benchmark = AIBenchmark()
results = benchmark.run()
```

and you are good to go. There's a leaderboard / ranking system to analyze benchmark results [here](https://burnout-benchmark.com/)🌸
