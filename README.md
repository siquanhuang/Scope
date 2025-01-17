# Scope
This codebase is the official PyTorch implementation of our paper:

***Scope: On Detecting Constrained Backdoor Attacks in Federated Learning***

>**Abstract.** Upcoming

## Citation
Upcoming

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

