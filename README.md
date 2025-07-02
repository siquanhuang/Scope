# Scope
This codebase is the official PyTorch implementation of our paper:

***Scope: On Detecting Constrained Backdoor Attacks in Federated Learning***

>**Abstract.** Federated learning (FL) allows multiple clients to train an efficient deep-learning model collaboratively but is susceptible to backdoor attacks. Traditional detection-based defenses depend on specific metrics to distinguish client gradients. Defense-aware attackers exploit this by constraining attack gradients on these metrics to evade detection, leading to metric-constrained attacks. This paper concretely instantiates such threats and introduces cosine-constrained attacks, which successfully compromise advanced defenses based on cosine distance. To address the aforementioned challenge, we propose Scope, a novel defense that detects cosine-constrained attacks using cosine distance by exposing the constrained backdoor dimensions of attack gradients. Scope employs dimension-wise normalization and differential scaling to amplify the distinction between backdoor dimensions and benign or unused ones, countering sophisticated attackers’ attempts to obscure them. Moreover, we develop a novel clustering approach, namely Dominant Gradient Clustering (DGC), to isolate and eliminate backdoor gradients. Extensive experiments across various datasets, models, FL settings, and adversary scenarios demonstrate that Scope consistently outperforms existing defenses by a significant margin, especially against the cosine-constrained attack. Additionally, we present a Scope-tailored attack designed to evade Scope, but it remains ineffective even when maximizing stealthiness, further underscoring the robustness of Scope. We release our source code at: https://github.com/siquanhuang/Scope.

## Citation
```bash
@ARTICLE{10852410,
  author={Huang, Siquan and Li, Yijiang and Yan, Xingfu and Gao, Ying and Chen, Chong and Shi, Leyu and Chen, Biao and Ng, Wing W. Y.},
  journal={IEEE Transactions on Information Forensics and Security}, 
  title={Scope: On Detecting Constrained Backdoor Attacks in Federated Learning}, 
  year={2025},
  volume={20},
  number={},
  pages={3302-3315},
  keywords={Data models;Adaptation models;Servers;Measurement;Training;Federated learning;Prevention and mitigation;Euclidean distance;Computational modeling;Image edge detection;Federated learning;backdoor attack;malicious clients;backdoor detection;clustering method},
  doi={10.1109/TIFS.2025.3533899}}

```

## Data preparation

The backdoor dataset SouthWest Airlines for CIFAR10 is in the project. To get backdoor dataset Ardis for MNIST/EMNIST please see **[edgecase_backdoors](https://github.com/SanaAwan5/edgecase_backdoors)**, which is the official code of the Edge-case attack. 

## Usage

#### example command

The follow command is to conduct Scope (ous) defense to defend against Edge-case Cosine-constrained attack on CIFAR10.
```bash
python simulated_averaging.py \
--lr 0.02 \
--gamma 0.998 \
--num_nets 200 \
--fl_round 1000 \
--part_nets_per_round 10 \
--local_train_period 2 \
--adversarial_local_training_period 2 \
--dataset cifar10 \
--model vgg9 \
--fl_mode fixed-freq \
--defense_method scope \
--attack_method cosine_constrained \
--attack_case edge-case \
--model_replacement False \
--poison_type southwest \
--norm_bound 2 \
--device=cuda
```


## Acknowledgements

We thank **[edgecase_backdoors](https://github.com/SanaAwan5/edgecase_backdoors)** for their amazing open-sourced project! We just add our Scope defense to this project.

