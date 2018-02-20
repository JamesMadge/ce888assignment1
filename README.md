# CE888 Assignment 1

## Data

8 [data sets](https://github.com/JamesMadge/ce888assignment1/tree/master/data) have been captured, each comprised of 5000 instances formed from 4 concatenated sequential frames of [agents](http://models.tensorpack.com/OpenAIGym/) playing one of eight Atari games, namely; Asteroids, Battle Zone, *Breakout*, *Gopher*, *James Bond*, *Ms. Pacman*, *Road Runner* and *Tennis*. The first 50 instances of each data set have been uploaded to GitHib for the purposes of demonstration. The entire data is 0.5GiB and hence is stored and maintained locally.

Each data instance has the following descriptive name: 

<**observation**>-<**episode**>-<**tick**>-<**action**>.png

Where, **observation** is the number of the observation from 0->4999, **episode** is the game number incremented from zero if a new game is started while observations are being captured, **tick** observation number for the current episode, **action** the resulting action taken by the agent.

![Asteroids](https://raw.githubusercontent.com/JamesMadge/ce888assignment1/master/data/asteroids/49-0-49-2.png "TEXT")
![Battle Zone](https://raw.githubusercontent.com/JamesMadge/ce888assignment1/master/data/battle_zone/49-0-49-9.png "TEXT")

![Breakout](https://raw.githubusercontent.com/JamesMadge/ce888assignment1/master/data/breakout/49-0-49-1.png "TEXT")
![Gopher](https://raw.githubusercontent.com/JamesMadge/ce888assignment1/master/data/gopher/49-0-49-4.png "TEXT")

![James Bond](https://raw.githubusercontent.com/JamesMadge/ce888assignment1/master/data/james_bond/49-0-49-11.png "TEXT")
![Ms. Pacman](https://raw.githubusercontent.com/JamesMadge/ce888assignment1/master/data/ms_pacman/49-0-49-6.png "TEXT")

![Road Runner](https://raw.githubusercontent.com/JamesMadge/ce888assignment1/master/data/road_runner/49-0-49-17.png "TEXT")
![Tennis](https://raw.githubusercontent.com/JamesMadge/ce888assignment1/master/data/tennis/49-0-49-8.png "TEXT")

## Code

Minimal code was required to be written for Assignment 1, the provided sample code shown below was modified and incorporated into the `play_one_episode` function of TensorPack's [common.py](https://github.com/ppwwyyxx/tensorpack/blob/master/examples/DeepQNetwork/common.py) file within the DeepQNetwork example to capture data instances named in the format specified above. The resulting implementation can be found [here](https://github.com/JamesMadge/ce888assignment1/blob/master/common.py).

```python
from PIL import Image

stacker = np.empty((84, 0, 3),dtype="uint8")

for it in range(4):
    im = Image.fromarray(s[:, :, it*3:3*(it+1)])
    q = np.asarray(im)
    stacker = np.hstack((stacker, q))

im = Image.fromarray(stacker)
im.save("game_name-" + str(t) + ".png") # you need to define (t) somewhere so that you know which part of the game you are in. 
```