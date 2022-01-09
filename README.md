# Chess
Are there benefits from deliberately avoiding information in pairing algorithms?

The idea goes as follows: Imagine that we have an algorithm which pairs players. We want this pairing to be as good as possible based on a series of parameters θ (similar level, that players have not played each other before, that they have not aborted the game before, etc.). Moreover, players value both, the time and the quality of the match.

This pairing algorithm is potentially very time-consuming given that lots of parameters need to be factored in. Furthermore, we expect time to be increasing with number of players and games.

The portential surprising fact comes from the fact that some very undesirable events like playing an "unpolite player" are extremely unlikely when the number of players is high enough. As a result, very little might be lost in terms of quality when the algorithm does not even need take into account this parameters.

Main consequence being that, paradoxically, you might be able to reach a good match faster, the higher the number of players.

We are interested in several questions:

What is the equilibrium of the system, namely how many players will enter the pool? 
Can we program via ML the weight of the different parameters given players preferences? 
Do we get a return from not looking at these parameters from the very beggining or alternatively, shall we progressively reduce the weight of these parameters the higher the number of games?
