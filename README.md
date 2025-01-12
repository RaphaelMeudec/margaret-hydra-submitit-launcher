# Margaret-hydra-submitit-launcher

![GitHub Workflow Build Status](https://github.com/raphaelmeudec/margaret-hydra-submitit-launcher/workflows/Continuous%20testing/badge.svg)

A Margaret tailored Hydra submitit launcher based on [Hydra](https://hydra.cc/docs/intro/) and its [submitit-launcher plugin](https://hydra.cc/docs/plugins/submitit_launcher/).
Basically it extends the submitit-launcher plugin with defaults that make sense for Margaret.

## Install

This package can be installed from pypi:
```
pip install margaret-hydra-submitit-launcher
```

You can also install it from source:
```
git clone https://github.com/raphaelmeudec/margaret-hydra-submitit-launcher.git
cd margaret-hydra-submitit-launcher
pip install .
```

## Use

The primary use is with the `hydra-submitit-launch` command with your script name and the config type:
```
hydra-submitit-launch my_app.py dev
```

### Available configs
6 different configs are available:
- `dev`: with 2 hours, 1 gpu, and qos_gpu-dev.
- `t3`: with 20 hours, 1 gpu, and qos_gpu-t3.
- `t4`: with 100 hours, 1 gpu, and qos_gpu-t4.
- `4gpus_dev`: with 2 hours, 4 gpus, and qos_gpu-dev.
- `4gpus_t3`: with 20 hours, 4 gpus, and qos_gpu-t3.
- `4gpus_t4`: with 100 hours, 4 gpus, and qos_gpu-t4.

By default, all the configs select 32Gb GPUs, use a single node and use the gpu_p1 partition.

### Advanced configs
You can override the SLURM config, the same way you would with any hydra configuration.
The parameters you can override are defined in the `hydra-submitit-launcher` plugin [doc](https://hydra.cc/docs/plugins/submitit_launcher/#usage).

For example, if you want to use the gpu_p2 partition, you would need to do:
```
hydra-submitit-launch my_app.py dev hydra.launcher.setup=null hydra.launcher.partition=gpu_p2
```

## References
- Hydra: https://hydra.cc/docs/intro/
- submitit-launcher: https://hydra.cc/docs/plugins/submitit_launcher/
- submitit: https://github.com/facebookincubator/submitit
