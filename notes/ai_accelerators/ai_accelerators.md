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
<td><a href="https://www.graphcore.ai/">Graphcore's</a> IPU has 1216 independent <a href="https://www.graphcore.ai/products/ipu">processors</a>. GraphCore: In-House Software Stack called “Poplar” + Multi-threaded Dataflow Execution. <br />

<img src="img/ipu.png" width="70%">

IPUs have a structure which provides efficient massive compute parallelism hand in hand with huge memory bandwidth. Graph based processing will change the way data are processed. Poplar enables lowering Pytorch, Tensorflow, or ONNX-based models to an imperative, C++ compatible code, in favor of what the company termed as: “vertex programming”.

Reference: Graphcore - <a href="https://youtu.be/N0syxQlkpAg">What's Inside an IPU Chip?</a>
</td>
</tr>
<tr>
<td>Data Processing Unit (DPU)</td>
<td>dd</td>
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
<td>FPGAs support a wide computational spectrum by enabling bit-level configurability: the arithmetic units can be configured to implement functions that operate on numbers of arbitrary widths, and the on-chip memory blocks can be fused to construct memory spaces of varied sizes. FPGA == reconfigurability.</td>
</tr>
<tr>
<td>Coarse-Grained Reconfigurable Arrays (CGRAs)</td>
<td>CGRAs have a high degree of reconfigurability but at a coarser-granularity than FPGAs (they sacrifice the finer-grained bit-level configurability as it might not be necessary).

Reconfigurable Dataflow — Wave Computing, SambaNova, SimpleMachines. They describe a software-defined hardware approach in which the compiler determines the structures of computational datapaths and the behavior of on-chip memories. At the core of its architecture lies the “reconfigurable dataflow unit” (RDU). The RDU chip contains an array of compute units (called “PCUs”) and scratchpad memory units (called “PMUs”) organized in a 2D-mesh hierarchy interconnected with NoC (network-on-chip) switches the RDU accesses off-chip memory using a hierarchy of units called AGUs and CUs.
</td>
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
<td>Their “chip” is a single wafer, meaning no dissection, just keep all manufactured chips on the big piece of silicon, and this would be the chip. Compared to the A100, Cerebras’ second-generation WSE (WSE-2) houses 123x more cores, 1000x more memory at 56x more the size but more power consumption.</td>
</tr>
<tr>
<td>Photonic Integrated Circuit (PIC)</td>
<td>
LightMatter: Photonics-Based Analog Computing. They designed a systolic array-based that performs multiply-and-accumulate operations by manipulating the photonics input signals using phase-shift encoded as different phases in the light signal’s waves (similar to how signals are being modulated when they are sent over fiber optic cables). As photonics data flows at the speed of light, LightMatter’s chips can potentially perform matrix and vectorized operations at very high speeds and potentially orders of magnitude less power.


</td>
</tr>
<tr>
<td>Super Computer</td>
<td><a href="https://youtu.be/oRUcvu-liFM">Tesla Dojo</a></td>
</tr>
</table>
<br />

<img src="img/ai_acc.png" width="100%">

source: [microsoft](https://www.microsoft.com/en-us/research/uploads/prod/2017/08/HC29.22622-Brainwave-Datacenter-Chung-Microsoft-2017_08_11_2017.compressed.pdf)

Leading AI hardware startups developing  several custom AI chips : 	[cerebras](https://www.cerebras.net/product-system/), [SambaNoba](https://sambanova.ai/), [Habana](https://habana.ai/), [Groq](https://groq.com/), [Hailo](https://hailo.ai/), [Esperanto](https://www.esperanto.ai/). 

References: AI Accelerators — Part I: [Intro](https://medium.com/@adi.fu7/ai-accelerators-part-i-intro-822c2cdb4ca4), Part II: [Transistors and Pizza](https://medium.com/@adi.fu7/ai-accelerators-part-ii-transistors-and-pizza-or-why-do-we-need-accelerators-75738642fdaa) (or: Why Do We Need Accelerators)?, Part III: [Architectural Foundations](https://medium.com/@adi.fu7/ai-accelerators-part-iii-architectural-foundations-3f1f73d61f1f), Part IV: [The Very Rich Landscape](https://medium.com/@adi.fu7/ai-accelerators-part-iv-the-very-rich-landscape-17481be80917), Part V: [Final Thoughts](https://medium.com/@adi.fu7/ai-accelerators-part-v-final-thoughts-94eae9dbfafb) ; [Accelerating Persistent Neural Networks at Datacenter Scale](https://youtu.be/DbhAMiQ_yvs) - Back in the 1980s, 1990s, and early 2000s, there was the “RISC vs. CISC war” with x86-based Intel and AMD leading the CISC side and ARM’s ISA leading “camp RISC”. There are pros and cons for each approach, but ultimately and greatly due to the booming of ARM-based smartphones, RISC came at the upper hand for mobile devices. It is now also becoming more dominant in the cloud with the designs like Amazon’s ARM-based line of [AWS Graviton](https://aws.amazon.com/ec2/graviton/) processors. NVIDIA bought ARM.

ISA For AI - Domain specific ISAs (extended RISCs), Very-Long Instruction Word (VLIW) architectures, Systolic Arrays ( used by TPUs and NVIDIA Tensor cores), Reconfigurable Processors (FPGAs), Dataflow Processing Systems and Processing in Memory ( for near data processing / Neuromorphic Computing ). Startups working on Systolic Arrays + VLIW: TPUv1, Groq, and Habana (2 chips: Goya for inference and Gaudi for training, [Greco](https://habana.ai/inference/greco/)). RISC-Based AI Accelerators: Esperanto and TensTorrent, [NeuReality](https://www.neureality.ai/): TCO-Driven Approach to Eliminate System Overheads.