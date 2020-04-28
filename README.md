# Conway's Game of Life (Neural Network)
The great mathematician John Horton Conway (26 December 1937 – 11 April 2020) passed away due to Covid-19. He made contributions to many branches of recreational mathematics, most notably the invention of the cellular automaton called the Game of Life. To commemorate him, I tried to build up a deep learning model to learn the pattern evaluation of this game.
## Rule of Conway's Game of Life
The follwing states is copied from wikipedia page of [Conway's Game of Life](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life):

---
The universe of the Game of Life is an infinite, two-dimensional orthogonal grid of square cells, each of which is in one of two possible states, alive or dead, (or populated and unpopulated, respectively). Every cell interacts with its eight neighbours, which are the cells that are horizontally, vertically, or diagonally adjacent. At each step in time, the following transitions occur:

* Any live cell with fewer than two live neighbours dies, as if by underpopulation.
* Any live cell with two or three live neighbours lives on to the next generation.
* Any live cell with more than three live neighbours dies, as if by overpopulation.
* Any dead cell with exactly three live neighbours becomes a live cell, as if by reproduction.

---
We can change rules by assigning the number of live neighbors (n_rebirth) which ensures the cell live and rebirth. For example, the original rules is n_rebirth =3: the cell can live or rebirth with 3 (n_rebirth) live neighbours, and the live cell which can still survive with 2 (n_rebirth-1) live neighbors. We can change the rules by setting n_rebirth to be between 2 and 8.
## Goal
The goal of this project is using deep learning methods to train the machine to :

1. predict the pattern evolution without knowing the rule
2. infere the rules from the given pattern evolutions which are produced by different rules (the model doesn't know the rules in the beginning). 
## Pattern Evaluation Prediction
With the given sets of the initial patterns and the next generations,  building a model which can predict the next generations without knowing the rules. The CNN model is used. My implementation is the extension based on [the article](https://kylewbanks.com/blog/conways-game-of-life-convolutional-neural-network-keras) written by Kyle Banks.
## Pattern Evaluation Classification
With the given sets of the pattern evolution of Game of Life with different rules, building a model which can infer the rules. This is essentially a time-series classification problem. Therefore, the CNN–LSTM model with the Timedistributed
is used. We can achieve this by wrapping the entire CNN input model in a TimeDistributed layer. [The article](https://machinelearningmastery.com/cnn-long-short-term-memory-networks/) written by Jason Brownlee explains how to implement this kind of model very well.
## Reference

* Using a Convolutional Neural Network to Play Conway's Game of Life with Keras, by Kyle Banks
https://kylewbanks.com/blog/conways-game-of-life-convolutional-neural-network-keras
* Conway's Game of Life in Python
https://jakevdp.github.io/blog/2013/08/07/conways-game-of-life/
* CNN Long Short-Term Memory Networks, by Jason Brownlee
https://machinelearningmastery.com/cnn-long-short-term-memory-networks/
