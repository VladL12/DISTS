# Deep Image Structure and Texture Similarity (DISTS) Metric

This is the repository of paper []().


### Highlights
1. A full-reference IQA metric correlated well with human perception of image quality.
2. Robust to texture variance (e.g., evaluating the images generated by GANs).
3. Robust to mild geometric transformations (e.g., evaluating the image pair that are not strictly point-by-point aligned).
4. Perceptual optimization for image generation/restoration tasks. The proposed metric can be employed as the objective function in various optimization problems. (The best practice: pretrain with L1/L2 loss, then finetune with DISTS + GAN loss)
   

**It contains three implementation versions:** 
1. Pytorch [```DISTS_pt.py```](/DISTS_pytorch/DISTS_pt.py) (recommend)
2. Tensorflow [```DISTS_tf.py```](/DISTS_tensorflow/DISTS_tf.py) 
3. Matlab [```DISTS.m```](/DISTS_matlab/DISTS.m). 

#### ====== Pytorch ======
**Installation:** 
- ```pip install dists-pytorch```

**Requirements:** 
- Python>=3.6
- Pytorch>=1.0

**Usage:** 
```python
from DISTS_pytorch import DISTS
D = DISTS()
# calculate DISTS between X, Y (a batch of RGB images, data range: 0~1)
# X: (N,3,H,W) 
# Y: (N,3,H,W) 
dists_value = D(X, Y)
# set 'require_grad=True, batch_average=True' to get a scalar value as loss.
dists_loss = D(X, Y, require_grad=True, batch_average=True) 
dists_loss.backward()
```
or

```bash
git clone https://github.com/dingkeyan93/DISTS
cd DISTS_pytorch
python DISTS_pt.py --ref <ref_path> --dist <dist_path>
```


#### ====== Tensorflow ======

**Requirements:** 
- Python>=3.6
- Tensorflow>=1.15

**Usage:** 
```bash
git clone https://github.com/dingkeyan93/DISTS
cd DISTS_tensorflow
python DISTS_tf.py --ref <ref_path> --dist <dist_path>
```

#### ====== Matlab ======

**Requirements:** 
- Matlab>=2019b

**Usage:** 
```bash
git clone https://github.com/dingkeyan93/DISTS
run demo.m
help DISTS
```

### Citation
```
@article{ding2020iqa,
  title={Image Quality Assessment: Unifying Structure and Texture Similarity},
  author={Ding, Keyan and Ma, Kede and Wang, Shiqi and Simoncelli, Eero P.},
  journal = {CoRR, abs/},
  volume = {},
  year={2020},
  url = {https://arxiv.org/abs/}
}
```

