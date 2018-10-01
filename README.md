# txt_torcs
This repository incorporates serval common issues in the original [gym_torcs](https://github.com/ugo-nama-kun/gym_torcs) repository, including:

1) Support Text Mode training in practice mode [#48](https://github.com/ugo-nama-kun/gym_torcs/issues/48);
2) Support running multiple gym_torcs experiments on the same machine [#27](https://github.com/ugo-nama-kun/gym_torcs/issues/27);
3) Upgrade torcs to the latest version;
4) Display the car in the screen [#7](https://github.com/ugo-nama-kun/gym_torcs/issues/7).
5) Support different tracks training. The supported tracks can be found in [TORCS](http://xed.ch/help/torcs.html).

## Examples of PPO
A simple example of using PPO to train torcs:

```shell
python run_torcs.py --road_type g-track-1*road
```

## Examples of gym_torcs
```Python
from multigym_torcs import TorcsEnv

# each TorcsEnv object should be associated with a different port in the same machine
# text_model=False will require a window to display
env = TorcsEnv(vision=False, throttle=True, gear_change=False, \
               trackname='street-1*road', port=3102, text_mode=True) 
env.reset()
env.step(env.action_space.sample())
```

``road_type`` or `trackname` in ``TorcsEnv`` consists of road_name and category name which are concatenated by `*`. 

For exmaple:
```
g-speedway*oval
```
Road and category names can be found in [TORCS](http://xed.ch/help/torcs.html).

## DISPLAY VISION Model on the remote server
If you want to run experiments and use vision mode on a remote server, personally I recommend to use `VirtualGL` and `TurboVNC`.
The setup files can be find [here](https://gist.github.com/cyberang3l/422a77a47bdc15a0824d5cca47e64ba2).


## Contact
Currently I only test for sensor based training, not on image-based training like original gym_torcs.
Please raise a issue if there is any bug or problem.
