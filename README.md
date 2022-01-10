# Chess
Are there benefits from deliberately avoiding information in pairing algorithms?

The idea goes as follows: Imagine that we have an algorithm which pairs players. We want this pairing to be as fast as possible, but also to take into account a series of parameters θ (level of the players, that players have not played each other before, that they have not aborted the game before, etc.). Moreover, players value both, the time and the quality of the match.

A traditional approach to these pairing algorithms is through search functions. There are two main types of algorithms: deterministic (those which break whenever the match is "good enough", as defined by the researcher) and stochastic time-based (those which break whenever the algorithm does not expect to find someone better than the current match in a finite time n). We will focus on the latter.

This pairing algorithm is potentially very time consuming given that lots of parameters need to be factored in. Furthermore, we expect time to be increasing with number of players and games, as the probability of finding someone significantly better, by just searching a bit more is relatively high when number of players is large enough.

The portential surprising fact comes from the fact that some very undesirable events like playing an "unpolite player" or playing a player "who has aborted you a game in the past" are extremely unlikely when the number of players is high. As a result, very little might be lost in terms of quality when the algorithm does not look at this parameters.

Main consequence being that, paradoxically, you might be able to reach a good match faster (under stochastic time-driven algorithms), the higher the number of players.

We are interested in several questions:

What is the equilibrium of the system, namely how many players will enter the pool? 
Can we program via ML the weight of the different parameters given players preferences? 
Do we get a return from not looking at these parameters from the very beggining or alternatively, shall we progressively reduce the weight of these parameters the higher the number of games?
