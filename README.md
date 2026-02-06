# Taking the neural sampling code very seriously

Code for the paper “Taking the neural sampling code very seriously: A data-driven approach for evaluating generative models of the visual system” (NeurIPS 2023).

Authors: Suhas Shrinivasan, Konstantin-Klemens Lurz, Kelli Restivo, George Denfield, Andreas Tolias, Edgar Walker, Fabian H. Sinz.

This repository provides a data-driven framework for learning and evaluating generative models of the visual system using neural responses and natural images. The generative model is composed of three components:

- Prior
- Likelihood
- Posterior

The scientific details are described in the paper; this repository contains the implementation and experiments.

## Project structure

- [neural_sampling_code](neural_sampling_code): Core library (dataloaders, loss functions, layers, trainers, evaluation utilities, etc.).
- [gensn_experiments/monkey/prior](gensn_experiments/monkey/prior): Prior experiments.
- [gensn_experiments/monkey/likelihood](gensn_experiments/monkey/likelihood): Likelihood experiments.
- [gensn_experiments/monkey/posterior](gensn_experiments/monkey/posterior): Posterior experiments.
- [database](database): DataJoint schemas and tables.

All experiments are managed using DataJoint: https://www.datajoint.com

The project uses PyTorch and a custom probabilistic ML library called gensn:

- https://github.com/walkerlab/gensn
- https://github.com/suhasshrinivasan/gensn

## Quick start (Docker)

The Docker setup contains all dependencies. Build and start the environment with:

```bash
docker compose -d --build
```

The project expects a host data folder mounted to /data/ inside the container (see [docker-compose.yml](docker-compose.yml)). This folder should contain the natural images and electrophysiological recordings used in the experiments. The work uses monkey V1 responses to natural images collected for:

Santiago Cadena et al., “Deep convolutional models improve predictions of macaque V1 responses to natural images.”

## Usage overview

1. Start the Docker environment.
2. Use DataJoint schemas in [database](database) to manage data and experiment tracking.
3. Run experiments from the corresponding folders under [gensn_experiments/monkey](gensn_experiments/monkey), depending on whether you are training/evaluating prior, likelihood, or posterior models.

Each experiment directory contains a run_*_experiment entry point for training:

- Prior: run_dequant_prior_experiment
- Likelihood: run_likelihood_experiment
- Posterior: run_posterior_experiment

For concrete experiment scripts, see:

- [gensn_experiments/monkey/prior](gensn_experiments/monkey/prior)
- [gensn_experiments/monkey/likelihood](gensn_experiments/monkey/likelihood)
- [gensn_experiments/monkey/posterior](gensn_experiments/monkey/posterior)

## Citation

If you use this code, please cite:

```bibtex
@article{shrinivasan2023taking,
	title={Taking the neural sampling code very seriously: A data-driven approach for evaluating generative models of the visual system},
	author={Shrinivasan, Suhas and Lurz, Konstantin-Klemens and Restivo, Kelli and Denfield, George and Tolias, Andreas and Walker, Edgar and Sinz, Fabian},
	journal={Advances in Neural Information Processing Systems},
	volume={36},
	pages={21945--21959},
	year={2023}
}
```
