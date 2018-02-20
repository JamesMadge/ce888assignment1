# CE888 Assignment 1

TODO! Add instance image. Add link to the written code. Add link to data.

## Data

8 data sets have been captured, each comprised of 5000 instances formed from 4 concatenated sequential frames of [agents](http://models.tensorpack.com/OpenAIGym/) playing one of eight Atari games, namely; Asteroids, Battle Zone, *Breakout*, *Gopher*, *James Bond*, *Ms. Pacman*, *Road Runner* and *Tennis*. The first 50 instances of each data set have been uploaded to GitHib for the purposes of demonstration. The entire data is 0.5GiB and hence is stored and maintained locally.

Each data instance has the following descriptive name: 

<**observation**>-<**episode**>-<**tick**>-<**action**>.png

Where, **observation** is the number of the observation from 0->4999, **episode** is the game number incremented from zero if a new game is started while observations are being captured, **tick** observation number for the current episode, **action** the resulting action taken by the agent.

![alt text](X.png "TEXT")

## Code

Minimal code was required to be written for Assignment 1, the provided sample code shown below was modified and incorporated into the `play_one_episode` function of [common.py](https://github.com/ppwwyyxx/tensorpack/blob/master/examples/DeepQNetwork/common.py) to capture data instances named in the format specified above. The resulting implementation can be found ...

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