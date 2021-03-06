# Performance

## Training Speedup
The following tables are comparisons of performance between different implementations of Transformers and optimizers, training on V100 and A100 with Transformer models with different number of layers. We use wps (words per second) to measure the speed.

### PyTorch

**6e6d (one V100)**

| batch_tokens | Fairseq | Fairseq+Apex | Fairseq+LightSeq | Fairseq+Apex speedup | Fairseq+LightSeq speedup |
|--------------|---------|--------------|------------------|----------------------|--------------------------|
| 512          | 3781    | 4677         | 11631            | 1.24                 | 3.08                     |
| 1024         | 8031    | 10270        | 19305            | 1.28                 | 2.40                     |
| 2048         | 16061   | 19646        | 28623            | 1.22                 | 1.78                     |
| 4096         | 23451   | 27664        | 35712            | 1.18                 | 1.52                     |
| 8192         | 28794   | 32134        | 40454            | 1.12                 | 1.40                     |
| 15000        | 31753   | 34220        | 43392            | 1.08                 | 1.37                     |


**6e6d (eight V100s)**

| batch_tokens | Fairseq | Fairseq+Apex | Fairseq+LightSeq | Fairseq+Apex speedup | Fairseq+LightSeq speedup |
|--------------|---------|--------------|------------------|----------------------|--------------------------|
| 512          | 26005   | 31274        | 61864            | 1.20                 | 2.38                     |
| 1024         | 58071   | 67710        | 111858           | 1.17                 | 1.93                     |
| 2048         | 106271  | 130152       | 182868           | 1.22                 | 1.72                     |
| 4096         | 167008  | 192741       | 245646           | 1.15                 | 1.47                     |
| 8192         | 208873  | 224161       | 292932           | 1.07                 | 1.40                     |
| 15000        | 237337  | OOM          | 323812           | N/A                  | 1.36                     |


**6e6d (eight A100s)**

| batch_tokens | Fairseq | Fairseq+Apex | Fairseq+LightSeq | Fairseq+Apex speedup | Fairseq+LightSeq speedup |
|--------------|---------|--------------|------------------|----------------------|--------------------------|
| 512          | 33300   | 40800        | 102400           | 1.23                 | 3.08                     |
| 1024         | 76500   | 85300        | 195400           | 1.12                 | 2.55                     |
| 2048         | 166100  | 182900       | 343900           | 1.10                 | 2.07                     |
| 4096         | 283800  | 324500       | 495700           | 1.14                 | 1.75                     |
| 8192         | 386500  | 421600       | 610200           | 1.09                 | 1.58                     |
| 15000        | 445600  | 500100       | 683100           | 1.12                 | 1.53                     |

---
**12e12d (eight V100s)**

| batch_tokens | Fairseq | Fairseq+Apex | Fairseq+LightSeq | Fairseq+Apex speedup | Fairseq+LightSeq speedup |
|--------------|---------|--------------|------------------|----------------------|--------------------------|
| 512          | 11616   | 15439        | 35848            | 1.33                 | 3.09                     |
| 1024         | 31628   | 35320        | 63355            | 1.12                 | 2.00                     |
| 2048         | 60279   | 70085        | 102594           | 1.16                 | 1.70                     |
| 4096         | 91947   | 106974       | 136899           | 1.16                 | 1.49                     |
| 8192         | OOM     | OOM          | 160846           | N/A                  | N/A                      |
| 15000        | OOM     | OOM          | OOM              | N/A                  | N/A                      |


**12e12d (eight A100s)**

| batch_tokens | Fairseq | Fairseq+Apex | Fairseq+LightSeq | Fairseq+Apex speedup | Fairseq+LightSeq speedup |
|--------------|---------|--------------|------------------|----------------------|--------------------------|
| 512          | 20300   | 22100        | 62100            | 1.09                 | 3.06                     |
| 1024         | 42500   | 46200        | 119100           | 1.09                 | 2.58                     |
| 2048         | 91100   | 104000       | 203100           | 1.14                 | 1.95                     |
| 4096         | 162600  | 182100       | 283300           | 1.12                 | 1.74                     |
| 8192         | 204200  | 236700       | 342600           | 1.16                 | 1.68                     |
| 15000        | OOM     | OOM          | OOM              | N/A                  | N/A                      |


---
**24e24d (eight V100s)**

| batch_tokens | Fairseq | Fairseq+Apex | Fairseq+LightSeq | Fairseq+Apex speedup | Fairseq+LightSeq speedup |
|--------------|---------|--------------|------------------|----------------------|--------------------------|
| 512          | 7276    | 8747         | 20418            | 1.20                 | 2.81                     |
| 1024         | 15916   | 17439        | 34892            | 1.10                 | 2.19                     |
| 2048         | 32687   | 38353        | 55411            | 1.17                 | 1.70                     |
| 4096         | OOM     | OOM          | OOM              | N/A                  | N/A                      |
| 8192         | OOM     | OOM          | OOM              | N/A                  | N/A                      |
| 15000        | OOM     | OOM          | OOM              | N/A                  | N/A                      |


**24e24d (eight A100s)**

| batch_tokens | Fairseq | Fairseq+Apex | Fairseq+LightSeq | Fairseq+Apex speedup | Fairseq+LightSeq speedup |
|--------------|---------|--------------|------------------|----------------------|--------------------------|
| 512          | 10300   | 11300        | 35600            | 1.10                 | 3.46                     |
| 1024         | 20800   | 23400        | 65300            | 1.13                 | 3.14                     |
| 2048         | 48100   | 54100        | 109300           | 1.12                 | 2.27                     |
| 4096         | 86100   | 96300        | 150100           | 1.12                 | 1.74                     |
| 8192         | OOM     | OOM          | OOM              | N/A                  | N/A                      |
| 15000        | OOM     | OOM          | OOM              | N/A                  | N/A                      |


### TensorFlow

**6e6d (one V100)**

| batch_tokens | NeurST | NeurST+LightSeq | NeurST+LightSeq speedup |
|--------------|--------|-----------------|-------------------------|
| 512          | 4765   | 9989            | 2.10                    |
| 1024         | 7066   | 14479           | 2.05                    |
| 2048         | 10157  | 21015           | 2.07                    |
| 4096         | 18499  | 27584           | 1.49                    |
| 8192         | 23776  | 33212           | 1.40                    |
| 15000        | 25677  | 35739           | 1.39                    |

**6e6d (eight V100s)**

| batch_tokens | NeurST | NeurST+LightSeq | NeurST+LightSeq speedup |
|--------------|--------|-----------------|-------------------------|
| 512          | 34761  | 54820           | 1.58                    |
| 1024         | 59561  | 94021           | 1.58                    |
| 2048         | 97843  | 149799          | 1.53                    |
| 4096         | 150378 | 198548          | 1.32                    |
| 8192         | 181475 | 241914          | 1.33                    |
| 15000        | 200358 | 267003          | 1.33                    |


## Kernel Speedup
The following tables are comparisons of performance between different implementations of CUDA kernels, running on one V100.

### Dropout

**fp32**

| total_counts (m) | PyTorch | TensorFlow | DeepSpeed | LightSeq |
|------------------|---------|------------|-----------|----------|
| 0.1              | 1.00    | 0.37       | 2.45      | 2.37     |
| 0.5              | 1.00    | 0.32       | 1.75      | 2.16     |
| 1                | 1.00    | 0.38       | 1.43      | 1.84     |
| 2                | 1.00    | 0.35       | 1.14      | 1.56     |
| 5                | 1.00    | 0.47       | 0.93      | 1.35     |
| 10               | 1.00    | 0.64       | 0.81      | 1.24     |
| 20               | 1.00    | 0.90       | 0.74      | 1.15     |
| 50               | 1.00    | 0.92       | 0.72      | 1.10     |
| 100              | 1.00    | 0.93       | 0.70      | 1.08     |

**fp16**

| total_counts (m) | PyTorch | TensorFlow | DeepSpeed | LightSeq |
|------------------|---------|------------|-----------|----------|
| 0.1              | 1.00    | 0.38       | 2.46      | 2.42     |
| 0.5              | 1.00    | 0.39       | 2.01      | 2.38     |
| 1                | 1.00    | 0.40       | 1.58      | 2.30     |
| 2                | 1.00    | 0.41       | 1.34      | 1.75     |
| 5                | 1.00    | 0.43       | 1.03      | 1.62     |
| 10               | 1.00    | 0.45       | 0.96      | 1.38     |
| 20               | 1.00    | 0.65       | 0.80      | 1.27     |
| 50               | 1.00    | 0.90       | 0.75      | 1.16     |
| 100              | 1.00    | 0.89       | 0.72      | 1.12     |

### Softmax

**fp32**

| batch_size | seq_len | PyTorch | TensorFlow | DeepSpeed | LightSeq |
|------------|---------|---------|------------|-----------|----------|
| 256        | 32      | 1.00    | 0.22       | 1.16      | 1.20     |
| 128        | 64      | 1.00    | 0.29       | 1.10      | 1.36     |
| 85         | 96      | 1.00    | 0.35       | 1.01      | 1.40     |
| 68         | 128     | 1.00    | 0.40       | 1.11      | 1.45     |
| 64         | 160     | 1.00    | 0.38       | 0.92      | 1.37     |
| 45         | 192     | 1.00    | 0.42       | 0.96      | 1.39     |
| 42         | 224     | 1.00    | 0.40       | 0.95      | 1.42     |
| 32         | 256     | 1.00    | 0.44       | 0.99      | 1.38     |
| 28         | 288     | 1.00    | 0.39       | 1.16      | 1.35     |
| 25         | 320     | 1.00    | 0.39       | 1.28      | 1.38     |

**fp16**

| batch_size | seq_len | PyTorch | TensorFlow | DeepSpeed | LightSeq |
|------------|---------|---------|------------|-----------|----------|
| 256        | 32      | 1.00    | 0.20       | 2.42      | 2.09     |
| 128        | 64      | 1.00    | 0.23       | 2.56      | 2.74     |
| 85         | 96      | 1.00    | 0.29       | 2.42      | 2.80     |
| 68         | 128     | 1.00    | 0.32       | 2.62      | 3.28     |
| 64         | 160     | 1.00    | 0.34       | 2.23      | 2.73     |
| 45         | 192     | 1.00    | 0.39       | 2.43      | 3.03     |
| 42         | 224     | 1.00    | 0.39       | 2.39      | 3.25     |
| 32         | 256     | 1.00    | 0.42       | 2.47      | 3.38     |
| 28         | 288     | 1.00    | 0.45       | 1.58      | 2.67     |
| 25         | 320     | 1.00    | 0.45       | 1.74      | 2.84     |
