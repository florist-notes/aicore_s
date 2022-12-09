# AI Accelerators
<img src="img/acc.png" width="40%"><a> </a><img src="img/acc2.png" width="49%">


Accelerate AI computations with : CPU = scalar, GPU = vector, IPU = graph >>>


<table style="width:100%" >
<tr>
<th>AI accelerator</th>
<th>Description</th>
</tr>
<tr>
<td>Tensor Processing Unit (TPU)</td>
<td>Tensor Processing Units (TPUs) are Google’s custom-developed application-specific integrated circuits (ASICs) used to accelerate machine learning workloads. <a href="https://en.wikipedia.org/wiki/Tensor_Processing_Unit">TPUs</a> are available for monthly <a href="https://cloud.google.com/tpu/pricing">subscription</a> by Google.

<a href="https://www.golem.de/news/machine-learning-googles-mini-tpu-kosten-mit-board-150-us-dollar-1903-139824.html">Edge TPU</a> (mini-TPU) for edge devices. This is the <a href="https://coral.ai/products/dev-board/">dev board</a> and <a href="https://shop.heise.de/google-coral-usb-accelerator">USB accelerator</a> for mini TPU. The TPU is 15 to 30 times faster than current GPUs. TPUs have high latency and are specifically built to target matrix multiplication (deep learning).

reference: <a href="https://cloud.google.com/blog/products/ai-machine-learning/an-in-depth-look-at-googles-first-tensor-processing-unit-tpu">An in-depth look at Google’s first Tensor Processing Unit (TPU)</a>.
</td>
</tr>
<tr>
<td>Intelligence Processing Unit (IPU)</td>
<td><a href="https://www.graphcore.ai/">Graphcore's</a> IPU has 1216 Independent <a href="https://www.graphcore.ai/products/ipu">processors</a>.

<img src="img/ipu.png" width="70%">

IPUs have a structure which provides efficient massive compute parallelism hand in hand with huge memory bandwidth. Graph based processing will change the way data are processed.

Reference: Graphcore - <a href="#">What's Inside an IPU Chip?</a>
</td>. 
</tr>
<tr>
<td>Vision Processing Unit (VPU)</td>
<td>dd</td>
</tr>
<tr>
<td>Quantum Processing Unit (QPU)</td>
<td>dd</td>
</tr>
<tr>
<td>Field-programmable gate array (FPGA)</td>
<td>dd</td>
</tr>
<tr>
<td>Application-specific integrated circuit (ASIC)</td>
<td>dd</td>
</tr>
<tr>
<td>System on a chip (SoC)</td>
<td>dd</td>
</tr>
<tr>
<td>Cerebras Wafer-Scale Engine (WSE)</td>
<td>dd</td>
</tr>
<tr>
<td>Photonic Integrated Circuit (PIC)</td>
<td>dd</td>
</tr>
<tr>
<td>Super Computer</td>
<td><a href="https://youtu.be/oRUcvu-liFM">Tesla Dojo</a></td>
</tr>
</table>
<br />

Leading AI hardware startups developing  several custom AI chips : 	[cerebras](https://www.cerebras.net/product-system/), [SambaNoba](https://sambanova.ai/), [Habana](https://habana.ai/), [Groq](https://groq.com/), [Hailo](https://hailo.ai/), [Esperanto](https://www.esperanto.ai/). 

References: AI Accelerators — Part I: [Intro](https://medium.com/@adi.fu7/ai-accelerators-part-i-intro-822c2cdb4ca4), Part II: [Transistors and Pizza](https://medium.com/@adi.fu7/ai-accelerators-part-ii-transistors-and-pizza-or-why-do-we-need-accelerators-75738642fdaa) (or: Why Do We Need Accelerators)?, Part III: [Architectural Foundations](https://medium.com/@adi.fu7/ai-accelerators-part-iii-architectural-foundations-3f1f73d61f1f), Part IV: [The Very Rich Landscape](https://medium.com/@adi.fu7/ai-accelerators-part-iv-the-very-rich-landscape-17481be80917), Part V: [Final Thoughts](https://medium.com/@adi.fu7/ai-accelerators-part-v-final-thoughts-94eae9dbfafb)