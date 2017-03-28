PyScatWave
==========

CuPy/PyTorch Scattering implementation

A scattering network is a CNN with filters predefined to wavelets that are not learned and it can be used in vision task such as classification of images.

The software uses PyTorch + NumPy FFT on CPU, and PyTorch + CuPy + CuFFT on GPU.

We used PyTorch for running experiments in <https://arxiv.org/abs/1703.08961>,
but it should be trivial to copy Scattering outputs to CPU (or run on CPU and
convert to `numpy.ndarray` via `.numpy()`) to use with other frameworks,
e.g. Chainer, Theano or Tensorflow.

Previous version of the code can be found at <https://github.com/edouardoyallon/scatwave>

## Installation

The software was tested on Linux with anaconda Python 2.7 and
various GPUs, including Titan X and Titan X Pascal.

The first step is to install pytorch following instructions from
<http://pytorch.org>, then you can run `pip`:

```
pip install -r requirements.txt
python setup.py install
```

## Usage

Example:

```python
import torch
from scatwave.scattering import Scattering

scat = Scattering(M=32, N=32, J=2).cuda()
x = torch.randn(1, 3, 32, 32).cuda()

print scat(x).size()
```


## Contribution

All contributions are welcome.


## Authors

Edouard Oyallon, Eugene Belilovsky, Sergey Zagoruyko
