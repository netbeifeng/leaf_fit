<div align="center">
<h2>🌿 LeafFit: Plant Assets Creation from 3D Gaussian Splatting (EG2026)</h2>

[**Chang Luo**](http://netbeifeng.github.io/) · [**Umetani Nobuyuki**](https://cgenglab.github.io/en/authors/admin/)  

The University of Tokyo <br>

**Eurographics 2026**

<a href="https://arxiv.org/abs/2602.11577"><img src='https://img.shields.io/badge/arXiv-LeafFit 🌿-firebrick?logo=arxiv' alt='Arxiv'></a>
<a href="./pdf/paper.pdf"><img src='https://img.shields.io/badge/PDF-LeafFit 🌿-orange?logo=googledocs&logoColor=white' alt='PDF'></a>
<a href='https://netbeifeng.github.io/LeafFit/'><img src='https://img.shields.io/badge/Project_Page-LeafFit 🌿-green?logo=googlechrome&logoColor=white' alt='Project Page'></a>
<a href='https://www.youtube.com/watch?v=7l-g5TWmFyU'><img src='https://img.shields.io/badge/Video-LeafFit 🌿-red?logo=youtube' alt='Youtube Video'></a>
<p style=''> Code will release soon! </p>
</div>

[\[Arxiv\]](https://arxiv.org/abs/2602.11577)
[\[Paper\]](./pdf/paper.pdf) 
[\[Project Page\]](https://netbeifeng.github.io/LeafFit/) 
[\[Video\]](https://www.youtube.com/watch?v=7l-g5TWmFyU) 


![teaser](./imgs/teaser.png)

LeafFit is a pipeline that converts 3D Gaussian Splatting (3DGS) of plants into editable, instanced mesh assets compatible with game engines. To address the high memory footprint of 3DGS, we segment leaves and fit a template mesh to each instance via differentiable Moving Least Squares (MLS) deformation. This approach significantly reduces data size and enables parameter-level editing, with deformations evaluated on-the-fly using a vertex shader for efficient runtime performance.

![pipeline](./imgs/workflow.png)

## Install

```bash
conda create -n leaf_fit python=3.10.11 pip -y
conda activate leaf_fit
pip install torch==2.7.1 torchvision==0.22.1 torchaudio==2.7.1 --index-url https://download.pytorch.org/whl/cu118
pip install -r requirements.txt
CC=gcc-10 CXX=g++-10 pip install --no-build-isolation "git+https://github.com/facebookresearch/pytorch3d.git"
cd ./libs/diff_gaussian_rasterization && CC=gcc-10 CXX=g++-10 pip install --no-build-isolation -e .
```

## Data

We provide 8 smartphone-captured 3DGS pretrained datasets in the [`data`](./data/) folder. The collection comprises:

- **Elliptic Leaves:** Green Pepper (9), Rubber Tree (14), Golden Pothos (5), Black Pearl Pepper (11), Ruby Leaf (7), and White Flag Bush (27).
- **Complex Morphology:** Cotton Rose (multi-lobed, 12) and Lucky Bamboo (thin and elongated, 11).

*(Note: The number in parentheses denotes the leaf count.)*

### Custom Dataset
For custom datasets, you may train your own plant with [GoF](https://niujinshuchong.github.io/gaussian-opacity-fields/) and crop the plant from the trained gaussian as the input for our method by using a gaussian editor e.g. [SuperSplat](https://superspl.at/editor).

## Citation
```
TBD
```

## Reference
This project is based on several wonderful projects:
- Heat Method: https://www.cs.cmu.edu/~kmcrane/Projects/HeatMethod/
- Gaussian Opacity Fields: https://niujinshuchong.github.io/gaussian-opacity-fields/
- 2D Gaussian Splatting: https://surfsplatting.github.io/
- Bayesian Coherent Point Drift: https://github.com/ohirose/bcpd
