# GraphGym Experiments
This repository contains some of the results files from running various graphgym experiments on spice netlists.

## Viewing Experiment Results
Each experiment contains a few different numbers - one for each execution of the experiment w/ a fixed random seed. Within an individual execution, there are statistics collected on the training data and validation data (saved under `train/` and `val/`) as well as model checkpoints in `ckpt`. The experiment configuration is available under `config.yaml`.

If we would like to view the final training/validation accuracy, we can simply look at the last line of the stats.json files in the respective files. With `jq`, this looks like this:
```
tail -n 1 train/stats.json | jq '.accuracy'
```

## Running experiments
First, clone and install our fork of [graphgym](https://github.com/symbench/GraphGym). Then you can run experiments by running the following in the `run/` directory of the repository:
```
python main.py --cfg configs/omitted_classification/ctrl_embeddings.yaml --repeat 3
```
In this case, `ctrl_embeddings.yaml` is the experiment configuration and it is repeated with 3 different random seeds.
