
# AI-Benchmark Alpha

: [ai-benchmark alpha](https://ai-benchmark.com/alpha)



## CPU training:
<img src="alphacpu.png" width=100%>

## GPU training:

After CUDA and CuDNN setup:

```python
from ai_benchmark import AIBenchmark

benchmark = AIBenchmark()
results = benchmark.run()
```
