# Phoronix Test Suite:


The [Phoronix Test Suite](https://github.com/phoronix-test-suite/phoronix-test-suite/blob/master/documentation/phoronix-test-suite.md) is the most comprehensive testing and benchmarking platform available for Linux, Solaris, macOS, Windows, and BSD operating systems. The Phoronix Test Suite allows for carrying out tests in a fully automated manner from test installation to execution and reporting.

```
    $ sudo apt-get install phoronix-test-suite 
```
In Red Hat based systems:
```
    $ yum install wget php-cli php-xml bzip2
    $ wget https://phoronix-test-suite.com/releases/phoronix-test-suite-10.8.4.tar.gz
    $ tar xvfz phoronix-test-suite-10.8.4.tar.gz
    $ cd phoronix-test-suite
    $ sudo ./install-sh

    Executable File: /usr/bin/phoronix-test-suite
    Documentation: /usr/share/doc/phoronix-test-suite/
    Phoronix Test Suite Files: /usr/share/phoronix-test-suite/

    $ /usr/bin/phoronix-test-suite list-available-tests (to see all available tests)
    $ /usr/bin/phoronix-test-suite list-available-suites (list all available suites)
    $ phoronix-test-suite list-recommended-tests


```

<table style="width:100%" >
<tr>
<th>Command</th>
<th>Description of Command</th>
</tr>
<tr>
<td>yum install phoronix-test-suite</td>
<td>This command will install phoronix-test-suite on the server.</td>
</tr>
<tr>
<td>yum remove phoronix-test-suite</td>
<td>This command will un-install phoronix-test-suite on the server. When you run this command, you will be asked if you are sure that you want to remove phoronix-test-suite, so you have to manually confirm that you want to do this.</td>
</tr>
<tr>
<td>yum -y remove phoronix-test-suite</td>
<td>This command will un-install phoronix-test-suite on the server. When you run this command with th e -y flag, you will not be prompted to check that you are sure you want to remove the package - so be sure you absolutely want to remove phoronix-test-suite when using the -y flag.</td>
</tr>
<tr>
<td>yum update phoronix-test-suite</td>
<td>This command will update phoronix-test-suite to the latest version. When you run this command, you will be asked if you are sure that you want to remove phoronix-test-suite, so you have to manually confirm that you want to do this.</td>
</tr>
<tr>
<td>yum -y update phoronix-test-suite</td>
<td>This command will update phoronix-test-suite to the latest version. When you run this command with the -y flag, you will not be prompted to check that you are sure you want to remove the package - so be sure you absolutely want to remove phoronix-test-suite when using the -y flag.</td>
</tr>
<tr>
<td>yum info phoronix-test-suite</td>
<td>This command will show you core information about the phoronix-test-suite package.</td>
</tr>
<tr>
<td>yum deplist phoronix-test-suite</td>
<td>This command will show you the dependencies for phoronix-test-suite. Thankfully, when using Yum, if dependencies are required, these are also installed at the same time so you don't have to worry too much about that.</td>
</tr>
<tr>
<td>yum check-update phoronix-test-suite</td>
<td>This command will check if there is an update waiting on phoronix-test-suite. When you run this command this will return nothing if there is nothing to update, or, will return the package name if the package is due to be updated.</td>
</tr>
</table>

```
$ phoronix-test-suite benchmark sysbench

RESULTS:

System Information


  PROCESSOR:              AMD Ryzen Threadripper PRO 5995WX 64-Cores @ 2.70GHz
    Core Count:           64                                        
    Thread Count:         128                                       
    Extensions:           SSE 4.2 + AVX2 + AVX + RDRAND + FSGSBASE  
    Cache Size:           256 MB                                    
    Microcode:            0xa008204                                 
    Core Family:          Family 25 Model 8                         
    Scaling Driver:       acpi-cpufreq performance (Boost: Enabled) 

  GRAPHICS:               NVIDIA GA102GL [RTX A5500] 24GB
    BAR1 / Visible vRAM:  256 MiB          
    Display Driver:       NVIDIA           
    Screen:               1920x1080        

  MOTHERBOARD:            LENOVO 1046
    BIOS Version:         S07KT4AA                         
    Chipset:              AMD Starship/Matisse             
    Audio:                NVIDIA GA102 HD Audio            
    Network:              2 x Aquantia AQC107 NBase-T/IEEE 

  MEMORY:                 256GB

  DISK:                   2 x 4097GB Kioxia KXG7APN84T09 LA
    File-System:          xfs 


$ phoronix-test-suite benchmark stress-ng
$ phoronix-test-suite benchmark pgbench ( PostgreSQL read, and read-write tests using the pgbenchsuite. )

```

Phoronix stores all its files in the directory ~/.phoronix-test-suite. This directory contains several files that include:

```
installed-tests
test-profiles
test-suites
test-results – If you saved the results, they are typically stored here in XML files, as well as SVGs
```
`$ cd ~/.phoronix-test-suite` > `$ cat test-results/mem/composite.xml` > `$ phoronix-test-suite result-file-to-json mem` > `phoronix-test-suite start-result-viewer `

openbenchmark uploads : `$ phoronix-test-suite openbenchmarking-uploads` and `phoronix-test-suite upload-result mytest`. To check recently added tests : `$ phoronix-test-suite recently-added-tests` and `$ phoronix-test-suite batch-setup` for batch benchmark.


## Available tests:
```
Available Tests

pts/ai-benchmark               - AI Benchmark Alpha                      System   
pts/aircrack-ng                - Aircrack-ng                             Processor
pts/amg                        - Algebraic Multi-Grid Benchmark          Processor
pts/aobench                    - AOBench                                 Processor
pts/aom-av1                    - AOM AV1                                 Processor
pts/apache                     - Apache HTTP Server                      System   
pts/apache-siege               - Apache Siege                            System   
pts/appleseed                  - Appleseed                               System   
pts/arrayfire                  - ArrayFire                               Processor
pts/askap                      - ASKAP                                   System   
pts/asmfish                    - asmFish                                 Processor
pts/astcenc                    - ASTC Encoder                            System   
pts/avifenc                    - libavif avifenc                         Processor
pts/basemark                   - Basemark GPU                            System   
pts/basis                      - Basis Universal                         System   
pts/blake2                     - BLAKE2                                  Processor
pts/blender                    - Blender                                 System   
pts/blogbench                  - BlogBench                               Disk     
pts/blosc                      - C-Blosc                                 Processor
pts/bork                       - Bork File Encrypter                     Processor
pts/botan                      - Botan                                   Processor
pts/brl-cad                    - BRL-CAD                                 System   
pts/build-apache               - Timed Apache Compilation                Processor
pts/build-clash                - Timed Clash Compilation                 Processor
pts/build-eigen                - Timed Eigen Compilation                 Processor
pts/build-erlang               - Timed Erlang/OTP Compilation            Processor
pts/build-ffmpeg               - Timed FFmpeg Compilation                Processor
pts/build-gcc                  - Timed GCC Compilation                   Processor
pts/build-gdb                  - Timed GDB GNU Debugger Compilation      Processor
pts/build-gem5                 - Timed Gem5 Compilation                  Processor
pts/build-godot                - Timed Godot Game Engine Compilation     Processor
pts/build-imagemagick          - Timed ImageMagick Compilation           Processor
pts/build-linux-kernel         - Timed Linux Kernel Compilation          Processor
pts/build-llvm                 - Timed LLVM Compilation                  Processor
pts/build-mesa                 - Timed Mesa Compilation                  Processor
pts/build-mplayer              - Timed MPlayer Compilation               Processor
pts/build-nodejs               - Timed Node.js Compilation               Processor
pts/build-php                  - Timed PHP Compilation                   Processor
pts/build-python               - Timed CPython Compilation               Processor
pts/build-wasmer               - Timed Wasmer Compilation                Processor
pts/build2                     - Build2                                  Processor
pts/bullet                     - Bullet Physics Engine                   Processor
pts/byte                       - BYTE Unix Benchmark                     Processor
pts/c-ray                      - C-Ray                                   Processor
pts/cachebench                 - CacheBench                              Processor
pts/caffe                      - Caffe                                   System   
pts/cassandra                  - Apache Cassandra                        System   
pts/chia-vdf                   - Chia Blockchain VDF                     Processor
pts/clickhouse                 - ClickHouse                              System   
pts/clomp                      - CLOMP                                   Processor
pts/cloudsuite-da              - CloudSuite Data Analytics               System   
pts/cloudsuite-ga              - CloudSuite Graph Analytics              System   
pts/cloudsuite-ma              - CloudSuite In-Memory Analytics          System   
pts/cloudsuite-ms              - CloudSuite Media Streaming              System   
pts/cloudsuite-ws              - CloudSuite Web Serving                  System   
pts/cloverleaf                 - CloverLeaf                              Processor
pts/clpeak                     - clpeak                                  System   
pts/cockroach                  - CockroachDB                             System   
pts/comd-cl                    - CoMD OpenCL                             System   
pts/compilebench               - Compile Bench                           Disk     
pts/compress-7zip              - 7-Zip Compression                       Processor
pts/compress-gzip              - Gzip Compression                        Processor
pts/compress-lz4               - LZ4 Compression                         Processor
pts/compress-pbzip2            - Parallel BZIP2 Compression              Processor
pts/compress-rar               - RAR Compression                         System   
pts/compress-xz                - XZ Compression                          Processor
pts/compress-zstd              - Zstd Compression                        Processor
pts/core-latency               - Core-Latency                            Processor
pts/coremark                   - Coremark                                Processor
pts/couchdb                    - Apache CouchDB                          System   
pts/cp2k                       - CP2K Molecular Dynamics                 Processor
pts/cpp-perf-bench             - CppPerformanceBenchmarks                System   
pts/cpuminer-opt               - Cpuminer-Opt                            Processor
pts/crafty                     - Crafty                                  Processor
pts/cryptopp                   - Crypto++                                Processor
pts/ctx-clock                  - ctx_clock                               System   
pts/cyclictest                 - Cyclictest                              System   
pts/cython-bench               - Cython Benchmark                        Processor
pts/dacapobench                - DaCapo Benchmark                        Processor
pts/daphne                     - Darmstadt Automotive Parallel Heterogeneous Suite System   
pts/dav1d                      - dav1d                                   Processor
pts/dbench                     - Dbench                                  Disk     
pts/deepsparse                 - Neural Magic DeepSparse                 System   
pts/deepspeech                 - DeepSpeech                              Processor
pts/dolfyn                     - Dolfyn                                  Processor
pts/draco                      - Google Draco                            System   
pts/dragonflydb                - Dragonflydb                             System   
pts/ebizzy                     - ebizzy                                  Processor
pts/ecp-candle                 - ECP-CANDLE                              System   
pts/embree                     - Embree                                  Processor
pts/encode-flac                - FLAC Audio Encoding                     Processor
pts/encode-mp3                 - LAME MP3 Encoding                       Processor
pts/encode-opus                - Opus Codec Encoding                     Processor
pts/encode-wavpack             - WavPack Audio Encoding                  System   
pts/encodec                    - EnCodec                                 System   
pts/espeak                     - eSpeak-NG Speech Engine                 Processor
pts/etcd                       - etcd                                    System   
pts/etcpak                     - Etcpak                                  Processor
pts/ethr                       - Ethr                                    Network  
pts/etqw-demo-iqc              - ET: Quake Wars Image Quality            System   
pts/fast-cli                   - fast-cli                                Network  
pts/ffmpeg                     - FFmpeg                                  Processor
pts/ffte                       - FFTE                                    Processor
pts/fftw                       - FFTW                                    Processor
pts/fhourstones                - Fhourstones                             Processor
pts/financebench               - FinanceBench                            System   
pts/fio                        - Flexible IO Tester                      Disk     
pts/fs-mark                    - FS-Mark                                 Disk     
pts/gcrypt                     - Gcrypt Library                          Processor
pts/geekbench                  - Geekbench                               System   
pts/git                        - Git                                     System   
pts/glibc-bench                - Glibc Benchmarks                        OS       
pts/gmpbench                   - GNU GMP GMPbench                        Processor
pts/gnupg                      - GnuPG                                   System   
pts/go-benchmark               - Go Benchmarks                           Processor
pts/gpaw                       - GPAW                                    System   
pts/graph500                   - Graph500                                System   
pts/graphics-magick            - GraphicsMagick                          Processor
pts/gromacs                    - GROMACS                                 System   
pts/hackbench                  - Hackbench                               Processor
pts/hammerdb-mariadb           - HammerDB - MariaDB                      System   
pts/hammerdb-postgresql        - HammerDB - PostgreSQL                   System   
pts/hbase                      - Apache HBase                            System   
pts/hdparm-read                - hdparm Timed Disk Reads                 Disk     
pts/helsing                    - Helsing                                 Processor
pts/himeno                     - Himeno Benchmark                        Processor
pts/hint                       - Hierarchical INTegration                System   
pts/hmmer                      - Timed HMMer Search                      Processor
pts/hpcc                       - HPC Challenge                           Processor
pts/hpcg                       - High Performance Conjugate Gradient     Processor
pts/idle                       - Timed Idle                              System   
pts/idle-power-usage           - Idle Power Usage                        System   
pts/incompact3d                - Xcompact3d Incompact3d                  Processor
pts/indigobench                - IndigoBench                             System   
pts/influxdb                   - InfluxDB                                System   
pts/intel-mlc                  - Intel Memory Latency Checker            Memory   
pts/intel-mpi                  - Intel MPI Benchmarks                    System   
pts/ior                        - IOR                                     Disk     
pts/ipc-benchmark              - IPC_benchmark                           Processor
pts/iperf                      - iPerf                                   Network  
pts/java-gradle-perf           - Java Gradle Build                       Processor
pts/java-jmh                   - Java JMH                                System   
pts/java-scimark2              - Java SciMark                            Processor
pts/jgfxbat                    - Java Graphics Basic Acceptance Test     Processor
pts/john-the-ripper            - John The Ripper                         Processor
pts/jpegxl                     - JPEG XL libjxl                          Processor
pts/jpegxl-decode              - JPEG XL Decoding libjxl                 Processor
pts/juliagpu                   - JuliaGPU                                System   
pts/keydb                      - KeyDB                                   System   
pts/kripke                     - Kripke                                  System   
pts/kvazaar                    - Kvazaar                                 Processor
pts/lammps                     - LAMMPS Molecular Dynamics Simulator     Processor
pts/lczero                     - LeelaChessZero                          Processor
pts/leveldb                    - LevelDB                                 Disk     
pts/libgav1                    - libgav1                                 Processor
pts/libraw                     - LibRaw                                  Processor
pts/liquid-dsp                 - Liquid-DSP                              Processor
pts/luajit                     - LuaJIT                                  Processor
pts/luaradio                   - LuaRadio                                Processor
pts/lulesh                     - LULESH                                  Processor
pts/lulesh-cl                  - Lulesh OpenCL                           System   
pts/luxcorerender              - LuxCoreRender                           Processor
pts/luxmark                    - LuxMark                                 System   
pts/lzbench                    - lzbench                                 Processor
pts/m-queens                   - m-queens                                Processor
pts/mafft                      - Timed MAFFT Alignment                   Processor
pts/mandelbulbgpu              - MandelbulbGPU                           System   
pts/mandelgpu                  - MandelGPU                               System   
pts/mbw                        - MBW                                     Memory   
pts/memcached                  - Memcached                               System   
pts/memtier-benchmark          - memtier_benchmark                       System   
pts/mencoder                   - Mencoder                                Processor
pts/minibude                   - miniBUDE                                Processor
pts/minife                     - miniFE                                  Processor
pts/minion                     - Minion                                  Processor
pts/mkl-dnn                    - oneDNN MKL-DNN                          Processor
pts/mlpack                     - Mlpack Benchmark                        System   
pts/mnn                        - Mobile Neural Network                   System   
pts/mocassin                   - Monte Carlo Simulations of Ionised Nebulae Processor
pts/montage                    - Montage Astronomical Image Mosaic Engine Processor
pts/mpcbench                   - GNU MPC                                 Processor
pts/mrbayes                    - Timed MrBayes Analysis                  Processor
pts/mt-dgemm                   - ACES DGEMM                              Processor
pts/multichase                 - Multichase Pointer Chaser               Processor
pts/mutex                      - BenchmarkMutex                          System   
pts/mysqlslap                  - MariaDB                                 System   
pts/n-queens                   - N-Queens                                Processor
pts/namd                       - NAMD                                    Processor
pts/natron                     - Natron                                  System   
pts/ncnn                       - NCNN                                    System   
pts/neat                       - Nebular Empirical Analysis Tool         Processor
pts/neatbench                  - NeatBench                               System   
pts/nekrs                      - nekRS                                   Processor
pts/nero2d                     - Open FMM Nero2D                         Processor
pts/netperf                    - Netperf                                 Network  
pts/nettle                     - Nettle                                  Processor
pts/network-loopback           - Loopback TCP Network Performance        Network  
pts/nginx                      - nginx                                   System   
pts/ngspice                    - Ngspice                                 Processor
pts/node-express-loadtest      - Node.js Express HTTP Load Test          Processor
pts/node-octane                - Node.js Octane Benchmark                Processor
pts/node-web-tooling           - Node.js V8 Web Tooling Benchmark        Processor
pts/novabench                  - Novabench                               System   
pts/npb                        - NAS Parallel Benchmarks                 Processor
pts/numenta-nab                - Numenta Anomaly Benchmark               System   
pts/numpy                      - Numpy Benchmark                         Processor
pts/nuttcp                     - Nuttcp                                  Network  
pts/nwchem                     - NWChem                                  Processor
pts/oidn                       - Intel Open Image Denoise                Processor
pts/oneapi-level-zero          - oneAPI Level Zero Tests                 System   
pts/onednn                     - oneDNN                                  Processor
pts/onnx                       - ONNX Runtime                            System   
pts/open-porous-media          - Open Porous Media                       Processor
pts/opencv                     - OpenCV                                  System   
pts/opencv-bench               - OpenCV Benchmark                        Processor
pts/opendwarfs                 - OpenDwarfs                              System   
pts/openems                    - OpenEMS                                 System   
pts/openfoam                   - OpenFOAM                                Processor
pts/openjpeg                   - OpenJPEG                                Processor
pts/openradioss                - OpenRadioss                             Processor
pts/openssl                    - OpenSSL                                 Processor
pts/openvino                   - OpenVINO                                System   
pts/openvkl                    - OpenVKL                                 Processor
pts/optcarrot                  - Optcarrot                               System   
pts/osbench                    - OSBench                                 OS       
pts/ospray                     - OSPRay                                  Processor
pts/ospray-studio              - OSPRay Studio                           Processor
pts/parboil                    - Parboil                                 Processor
pts/pennant                    - Pennant                                 Processor
pts/perf-bench                 - perf-bench                              OS       
pts/perl-benchmark             - Perl Benchmarks                         Processor
pts/pgbench                    - PostgreSQL                              System   
pts/php                        - PHP Micro Benchmarks                    System   
pts/phpbench                   - PHPBench                                System   
pts/pjdfstest                  - Pjdfstest                               Disk     
pts/pjsip                      - PJSIP                                   Processor
pts/plaidml                    - PlaidML                                 System   
pts/pmbench                    - pmbench                                 Memory   
pts/polybench-c                - PolyBench-C                             Processor
pts/polyhedron                 - Polyhedron Fortran Benchmarks           Processor
pts/postmark                   - PostMark                                Disk     
pts/povray                     - POV-Ray                                 Processor
pts/powertop-wakeups           - Powertop Wakeups                        Processor
pts/primesieve                 - Primesieve                              Processor
pts/pts-self-test              - Phoronix Test Suite Self Test           System   
pts/pybench                    - PyBench                                 System   
pts/pyhpc                      - PyHPC Benchmarks                        System   
pts/pymongo-inserts            - PyMongo Inserts                         System   
pts/pyperformance              - PyPerformance                           System   
pts/qmcpack                    - QMCPACK                                 Processor
pts/qmlbench                   - Qmlbench                                System   
pts/quadray                    - QuadRay                                 Processor
pts/quantlib                   - QuantLib                                Processor
pts/radiance                   - Radiance Benchmark                      Processor
pts/ramspeed                   - RAMspeed SMP                            Memory   
pts/rav1e                      - rav1e                                   Processor
pts/rays1bench                 - rays1bench                              Processor
pts/rbenchmark                 - R Benchmark                             Processor
pts/redis                      - Redis                                   System   
pts/relion                     - RELION                                  Processor
pts/renaissance                - Renaissance                             Processor
pts/rnnoise                    - RNNoise                                 Processor
pts/rocksdb                    - RocksDB                                 System   
pts/rodinia                    - Rodinia                                 Processor
pts/rust-mandel                - Rust Mandelbrot                         Processor
pts/rust-prime                 - Rust Prime Benchmark                    Processor
pts/schbench                   - Schbench                                System   
pts/scikit-learn               - Scikit-Learn                            System   
pts/scimark2                   - SciMark                                 Processor
pts/securemark                 - SecureMark                              Processor
pts/serial-loopback            - Serial Loopback Test                    System   
pts/simdjson                   - simdjson                                Processor
pts/smallpt                    - Smallpt                                 Processor
pts/smallpt-gpu                - SmallPT GPU                             System   
pts/smart                      - SMART Disk Self-Report                  Disk     
pts/smhasher                   - SMHasher                                Processor
pts/sockperf                   - Sockperf                                OS       
pts/spacy                      - spaCy                                   System   
pts/spark                      - Apache Spark                            System   
pts/spec-cpu2017               - SPEC CPU 2017                           System   
pts/spec-jbb2015               - SPECjbb 2015                            System   
pts/speedtest-cli              - speedtest-cli                           Network  
pts/sqlite                     - SQLite                                  Disk     
pts/sqlite-speedtest           - SQLite Speedtest                        System   
pts/srslte                     - srsLTE                                  Processor
pts/srsran                     - srsRAN                                  Processor
pts/stargate                   - Stargate Digital Audio Workstation      Processor
pts/startup-time               - Application Start-up Time               Disk     
pts/stockfish                  - Stockfish                               Processor
pts/stream                     - Stream                                  Memory   
pts/stream-dynamic             - Stream-Dynamic                          Memory   
pts/stress-ng                  - Stress-NG                               System   
pts/stressapptest              - Stressful Application Test              Memory   
pts/sudokut                    - Sudokut                                 Processor
pts/sunflow                    - Sunflow Rendering System                System   
pts/svt-av1                    - SVT-AV1                                 Processor
pts/svt-hevc                   - SVT-HEVC                                Processor
pts/svt-vp9                    - SVT-VP9                                 Processor
pts/swet                       - Swet                                    Processor
pts/synthmark                  - Google SynthMark                        Processor
pts/sysbench                   - Sysbench                                System   
pts/system-decompress-bzip2    - System BZIP2 Decompression              Processor
pts/system-decompress-gzip     - System GZIP Decompression               Processor
pts/system-decompress-tiff     - System Libtiff Decompression            Processor
pts/system-decompress-xz       - System XZ Decompression                 Processor
pts/system-libjpeg             - System JPEG Library Decode              Processor
pts/system-libxml2             - System Libxml2 Parsing                  Processor
pts/systemd-boot-kernel        - Systemd Kernel Boot Time                Processor
pts/systemd-boot-total         - Systemd Total Boot Time                 System   
pts/systemd-boot-userspace     - Systemd Userspace Boot Time             Processor
pts/t-test1                    - t-test1                                 Memory   
pts/tachyon                    - Tachyon                                 Processor
pts/tensorflow                 - TensorFlow                              System   
pts/tensorflow-lite            - TensorFlow Lite                         System   
pts/tinymembench               - Tinymembench                            Memory   
pts/tiobench                   - Threaded I/O Tester                     Disk     
pts/tjbench                    - libjpeg-turbo tjbench                   System   
pts/tnn                        - TNN                                     System   
pts/toktx                      - KTX-Software toktx                      System   
pts/toybrot                    - toyBrot Fractal Generator               Processor
pts/tscp                       - TSCP                                    Processor
pts/ttsiod-renderer            - TTSIOD 3D Renderer                      Processor
pts/tungsten                   - Tungsten Renderer                       Processor
pts/unpack-firefox             - Unpacking Firefox                       System   
pts/unpack-linux               - Unpacking The Linux Kernel              Disk     
pts/uvg266                     - uvg266                                  Processor
pts/v-ray                      - Chaos Group V-RAY                       System   
pts/viennacl                   - ViennaCL                                System   
pts/vosk                       - VOSK Speech Recognition Toolkit         Processor
pts/vpxenc                     - VP9 libvpx Encoding                     Processor
pts/vvenc                      - VVenC                                   Processor
pts/webp                       - WebP Image Encode                       Processor
pts/webp2                      - WebP2 Image Encode                      Processor
pts/will-it-scale              - will-it-scale                           OS       
pts/wrf                        - WRF                                     System   
pts/x264                       - x264                                    Processor
pts/x265                       - x265                                    Processor
pts/xmrig                      - Xmrig                                   Processor
pts/xsbench                    - Xsbench                                 System   
pts/xsbench-cl                 - Xsbench OpenCL                          System   
pts/y-cruncher                 - Y-Cruncher                              Processor
pts/yafaray                    - YafaRay                                 Processor
system/apache                  - Apache Benchmark                                 
system/blender                 - Blender                                 System   
system/blogbench               - BlogBench                               Disk     
system/clpeak                  - clpeak                                  System   
system/compress-lzma           - LZMA Compression                                 
system/compress-pbzip2         - PBZIP2 Compression                               
system/compress-zstd           - Zstd Compression                        Processor
system/cryptsetup              - Cryptsetup                              System   
system/darktable               - Darktable                               System   
system/dbench                  - Dbench                                  Disk     
system/ethminer                - Ethereum Ethminer                       System   
system/fio                     - Flexible IO Tester                      Disk     
system/gegl                    - GEGL                                    System   
system/gimp                    - GIMP                                    System   
system/gmic                    - G'MIC                                   System   
system/gnupg                   - GnuPG                                   Processor
system/gnuradio                - GNU Radio                               Processor
system/hugin                   - Hugin                                   System   
system/inkscape                - Inkscape                                System   
system/iozone                  - IOzone                                  Disk     
system/libreoffice             - LibreOffice                             System   
system/mpv                     - MPV                                     System   
system/nginx                   - Nginx                                   System   
system/ocrmypdf                - OCRMyPDF                                System   
system/octave-benchmark        - GNU Octave Benchmark                    System   
system/openscad                - OpenSCAD                                System   
system/openssl                 - OpenSSL                                 Processor
system/opm                     - Open Porous Media                       Processor
system/rawtherapee             - RawTherapee                             System   
system/redis                   - Redis Memtier / Redis Benchmark         System   
system/rsvg                    - librsvg                                 System   
system/selenium                - Selenium                                System   
system/selenium-top-sites      - Time To Load + View Popular Websites    System   
system/sqlite                  - SQLite                                           
system/tesseract-ocr           - Tesseract OCR                           System   
system/wireguard               - WireGuard + Linux Networking Stack Stress Test Network  

```


## Available suites:

```

Available Suites

  pts/audio-encoding               - Audio Encoding                   System
  pts/av1                          - AV1                              System
  pts/bioinformatics               - Bioinformatics                   System
  pts/browsers                     - Web Browsers                     System
  pts/cad                          - CAD                              System
  pts/chess                        - Chess Test Suite                 Processor
  pts/compilation                  - Timed Code Compilation           System
  pts/compiler                     - C/C++ Compiler Tests             Processor
  pts/compression                  - Compression Tests                Processor
  pts/computational                - Computational Test Suite         System
  pts/computational-biology        - Computational Biology Test Suite Processor
  pts/cpu                          - CPU / Processor Suite            Processor
  pts/cpu-massive                  - CPU Massive                      System
Updated OpenBenchmarking.org Repository Index
pts: 510 Distinct Tests, 85 Suites

Updated OpenBenchmarking.org Repository Index
system: 41 Distinct Tests, 1 Suites

* pts/creator                      - Creator Workloads                System
  pts/cryptocurrency               - Cryptocurrency Benchmarks, CPU Mining Tests Processor
  pts/cryptography                 - Cryptography                     Processor
  pts/daily-kernel-tracker         - Daily Kernel Tracker             System
  pts/daily-system-tracker         - Daily System Tracker             System
  pts/database                     - Database Test Suite              System
  pts/desktop-graphics             - Desktop Graphics                 System
  pts/disk                         - Disk Test Suite                  Disk
  pts/electronic-design            - Electronic Design                System
  pts/encoding                     - Encoding                         System
  pts/favorites                    - Favorites                        System
  pts/finance                      - Finance                          System
  pts/game-dev                     - Game Development                 System
  pts/gaming                       - Gaming                           System
  pts/gaming-closed                - Closed-Source Gaming             System
  pts/gaming-free                  - Free Software Gaming             System
  pts/gui-toolkits                 - GUI Toolkits                     Graphics
  pts/hpc                          - HPC - High Performance Computing System
  pts/imaging                      - Imaging                          System
  pts/internet-speed               - Internet Speed                   System
  pts/ioquake3-games               - Games Using The ioquake3 Engine  System
  pts/iqc                          - Image Quality Comparison Suite   Graphics
  pts/java                         - Java                             System
  pts/java-opengl                  - Java OpenGL                      System
  pts/kernel                       - Common Kernel Benchmarks         System
  pts/linear-algebra               - Linear Algebra                   System
  pts/linux-system                 - Linux System                     System
  pts/machine-learning             - Machine Learning                 System
  pts/memory                       - Memory Test Suite                Memory
  pts/mesa                         - Mesa Test Suite                  Graphics
  pts/molecular-dynamics           - Molecular Dynamics               System
  pts/motherboard                  - Motherboard                      System
  pts/mpi                          - MPI Benchmarks                   System
* pts/multicore                    - Multi-Core                       Processor
  pts/netbook                      - Netbook Test Suite               System
  pts/network                      - Networking Test Suite            Network
  pts/nevada                       - OpenSolaris Nevada Test Suite    System
  pts/nvidia-gpu-compute           - NVIDIA GPU Compute               Graphics
  pts/ocr                          - OCR                              System
  pts/oneapi                       - Intel oneAPI                     System
  pts/opencl                       - OpenCL                           System
  pts/opengl-demos                 - OpenGL Demos Test Suite          System
  pts/opengl-workstation           - OpenGL Workstation Test Suite    System
  pts/productivity                 - Productivity                     System
  pts/programmer                   - Programmer / Developer System Benchmarks System
  pts/pts-desktop-live             - PTS Desktop Live                 System
  pts/python                       - Python                           System
  pts/quantum-mechanics            - Quantum Mechanics                System
  pts/ray-tracing                  - Ray-Tracing Test Suite           System
  pts/raytracing                   - Raytracing                       System
* pts/renderers                    - Renderers                        Processor
  pts/scientific-computing         - Scientific Computing             System
  pts/sdr                          - Software Defined Radio           System
  pts/server                       - Server                           System
  pts/server-cpu-tests             - Server CPU Tests                 Processor
  pts/server-memory                - Server Memory                    Memory
  pts/single-threaded              - Single-Threaded                  System
  pts/speech                       - Speech                           System
  pts/steam                        - Steam                            Graphics
  pts/telephony                    - Telephony                        System
  pts/texture-compression          - Texture Compression              System
  pts/ue4                          - Unreal Engine 4 Tech Demos On Linux Graphics
  pts/unigine                      - Unigine Test Suite               Graphics
  pts/universe                     - Universe Test Suite              System
  pts/universe-cli                 - Universe CLI Test Suite          System
  pts/universe-x                   - Universe X Test Suite            System
  pts/video-encoding               - Video Encoding                   System
  pts/vulkan-compute               - Vulkan Compute                   Graphics
  pts/vulkan-rt                    - Vulkan Ray-Tracing               Graphics
  pts/workstation                  - Common Workstation Benchmarks    System
  pts/workstation-graphics         - Workstation Graphics             Graphics
  pts/xrender                      - X Render Extension Testing       Graphics
  system/collection                - Collection                       System

* Indicates a partially supported suite.


```

## Recommended OpenBenchmarking.org Test Profiles

```
System Tests

pts/apache                     - Apache HTTP Server                     
pts/pgbench                    - PostgreSQL                             
pts/nginx                      - nginx                                  
pts/blender                    - Blender                                
pts/redis                      - Redis                                  
pts/stress-ng                  - Stress-NG                              
system/selenium                - Selenium                               
pts/scikit-learn               - Scikit-Learn                           
pts/brl-cad                    - BRL-CAD                                
pts/tensorflow                 - TensorFlow                             

Processor Tests

pts/build-linux-kernel         - Timed Linux Kernel Compilation         
pts/ffmpeg                     - FFmpeg                                 
pts/x264                       - x264                                   
pts/compress-7zip              - 7-Zip Compression                      
pts/encode-flac                - FLAC Audio Encoding                    
pts/build-php                  - Timed PHP Compilation                  
pts/graphics-magick            - GraphicsMagick                         
pts/primesieve                 - Primesieve                             
pts/vpxenc                     - VP9 libvpx Encoding                    
pts/lammps                     - LAMMPS Molecular Dynamics Simulator    

Graphics Tests

pts/xonotic                    - Xonotic                                
pts/csgo                       - Counter-Strike: Global Offensive       
pts/unvanquished               - Unvanquished                           
pts/etlegacy                   - ET: Legacy                             
pts/unigine-super              - Unigine Superposition                  
pts/paraview                   - ParaView                               
pts/hitman                     - HITMAN                                 
pts/vkmark                     - VKMark                                 
pts/portal2                    - Portal 2                               
pts/gravitymark                - GravityMark                            

Network Tests

pts/ethr                       - Ethr                                   
pts/fast-cli                   - fast-cli                               
pts/speedtest-cli              - speedtest-cli                          

OS Tests

pts/glibc-bench                - Glibc Benchmarks                       
pts/perf-bench                 - perf-bench                             
pts/will-it-scale              - will-it-scale                          

Memory Tests

pts/stream                     - Stream                                 
pts/intel-mlc                  - Intel Memory Latency Checker           

Disk Tests

pts/unpack-linux               - Unpacking The Linux Kernel 

```