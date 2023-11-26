# Introduction
In this paper, we propose a more efficient, yet accurate Transformer model based on the TokenPose Transformer\cite{li2021tokenpose}, named Improve TokenPose with Sparsity. Specifically, we focus on two types of sparse tokens, human-joint keypoint tokens, and attention-level visual tokens. On keypoint tokens, we refer to human physiological structures to strengthen the connection of relevant joints with a sparse joint mask. On visual tokens, we introduce sparsity at the attention level by pruning attention connections. We reveal that pruning these sparse tokens does not reduce the accuracy but can accelerate the entire network. 
 
Our main contributions to the Improved TokenPose with Sparsity are summarized as follows:

1. We propose an attention-based pruning strategy to dynamically upgrade a sparse attention mask. By focusing on the more significant visual tokens, we can simultaneously achieve both token and attention connections during training while making use of their sparsities. Our method does not require a complex token selector module or additional training loss or hyper-parameters.
2. We propose a self-defined sparse joint mask based on human structure. With the use of graph degree, we can pre-define a 0-1 mask to emphasize the connections between adjacent joints and symmetrical joints.
3. We conduct extensive experiments on MPII dataset, and prove the feasibility of the method by experimental analysis.

# Quick use
## 1. Dependencies installation & data preparation
Please refer to [THIS](https://github.com/leoxiaobin/deep-high-resolution-net.pytorch) to prepare the environment step by step.

## 2. Trainging
### Training on MPII dataset 
```
python tools/train.py \
    --cfg experiments/mpii/tokenpose/tokenpose_l_D6_256x256_patch44_dim192_depth6.yaml\
```
## 3. Testing
### Testing on MPII dataset using TRAINED models
```
python tools/test.py \
    --cfg experiments/mpii/tokenpose/tokenpose_l_D6_256x256_patch44_dim192_depth6.yaml\
    TEST.MODEL_FILE _PATH_TO_CHECKPOINT_ 
```

# Citations
If you use our code or models in your research, please give it a star or cite with:
```
@inproceedings{li2021tokenpose,
  title={TokenPose: Learning Keypoint Tokens for Human Pose Estimation},
  author={Yanjie Li and Shoukui Zhang and Zhicheng Wang and Sen Yang and Wankou Yang and Shu-Tao Xia and Erjin Zhou},
  booktitle={IEEE/CVF International Conference on Computer Vision (ICCV)},
  year={2021}
}
```
# Acknowledgement
Thanks for the open-source:
> [HRNet](https://github.com/leoxiaobin/deep-high-resolution-net.pytorch/), [timm](https://github.com/rwightman/pytorch-image-models), [DarkPose](https://github.com/ilovepose/DarkPose), [DETR](https://github.com/facebookresearch/detr)
