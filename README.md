# neuralang

overview/plan: small neural-network-controlled beings learn to build walls communicate with "sound," through reinforcement learning or genetic algorithms. includes 2d physics built from scratch, rendered using the ggez crate.

![clip](https://github.com/user-attachments/assets/256634ee-c3f9-40af-9c13-5e1a535caa54)


---------------------------------
8/8/24: lots of additions, commit messages this time have been descriptive enough so I don't have to exposit here. although, hyperparameters need a LOT of tweaking to extract even arguably non-random behaviour such as food-seeking. need to make speaking and building a lot cheaper so they are not discouraged evolutionarily altogether. my humble laptop isn't able to run for the ns of thousands of generations I had envisioned for there to evolve any non-trivial behaviour. stands to be seen whether increasing model complexity can make a difference and produce decent behaviour despite small selection populations and rudimentary mutation and crossover.

2/8/24: lot has changed (my lot has changed too), took some effort to reenter the project headspace after almost a year of not looking at it. decided on Burn for NNs since I quite like the API and the relative lack of boilerplate. beings now collect all inputs they see in the wild each timestep, then convert them to tensors. what is left is to first build the baseline model, and since output-to-action mapping is already complete, begin letting the nns control the beings. it won't be any effort to implement a minimal selection scheme, and a minimal mutation system. after the prototype is fully functional can work on tweaking the details begin. if baseline models display even some sophistication, I will consider a full implementation of [Set Transformers](https://arxiv.org/abs/1810.00825). and if they don't, I will instead do it out of desperation. but this is way down the list. I imagine a lot of trials with different genetic algorithms, and selection schemes until something clicks, and importantly, making the beings past-sensitive as LSTMs to see if they start executing non-trivial plans. I think, since the idea of the set-transformer is opposed to history-processing by design, the ideal model will be a set-transformation of current-step inputs, to be fed into the LSTM.

~~current~~ ?/?/23: I'm able to simulate upwards of 40k objects at 60Hz, on a single thread. Instead of using theads to optimize a single simulation, since the rendering happens to be thread-safe, I want to run multiple simulation worlds, one per thread. Maybe lineages could be transferred between worlds to accelerate evolution. My gpu isn't all that beefy, so I guess for now 1-2 will have to suffice.

8/9/23: ~~Currently toying with the idea of having one large net control all the creatures as batched stimulus-actions. this would create very uniform behaviour and eliminate hostile behavior entirely but given the larger capacity it will likely show much better planning and sophistication. i will defer taking this route until I am absolutely certain that n single-sample forward passes can not be made as efficient as one n-batch pass. the obvious middle way is to have a few (say 5) medium sized models control fractions of the population, color coded.~~ no point.
