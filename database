
#*********************************************
# Author:       Carlos Gonzalez
# Date:         08/01/2021
# Description:  The present code creates a database of chess players
#               parameters
#********************************************


##Load packages
if (!require("tidyverse")) install.packages("tidyverse")
library(tidyverse)
  
## Data input
  rm(list = ls())
  set.seed(123)
  
  #Number of players
  n<-50
  
  #Elo stats
  mean_elo<-1700
  sd_elo<-400
  
  #Number of initial games
  games<-500
  
## Creation of database
  
  ## Creation of general profile of players
  profiles<-list()
  
  for (i in 1:n){
    
    ##Creation of individual profiles
    profile<-list()
    
    #profile[[1]] contains some basic stats of the player
    profile[[1]]<-data.frame(id_player=i, elo = floor(rnorm(1, mean = mean_elo, sd = sd_elo)), n_games = 0)
    
    #profile[[2]] contains details of all games
    profile[[2]]<-data.frame(id_rival=NA, result= NA, trash_talk=NA)
    profiles[[i]]<-profile
    
  }  
  
  ##Game simulation
  for (i in 1:games){
    
    ##Set different seed allow us not to infinitely repeat the same game, while being replicable
    set.seed(i)
    
    ##We choose the players
    players<-sample(1:n,2, replace = FALSE)
    
    ##We extract their elo to identify the probability of winning
    elo_1<-profiles[[players[1]]][[1]][["elo"]]
    elo_2<-profiles[[players[2]]][[1]][["elo"]]
    
    ##We normalize (the closer to zero, the more likely the victory of player 2)
    elo_norm<-pnorm(elo_1-elo_2,0,sd_elo)
  
    ##We randomize the probability of aborting game before starting
    result<-sample(c(NA,99), 1, prob = c(0.9, 0.1))
    
    ##We determine the outcome of the game (note, initially, we even assign a probability to aborted games)
    ##The intuition is that the probability of victory gets determined by the ELO difference
    ##Probability of draw is extracted in a similar fashion
    result_prov<-sample(c(0, 0.5,1), 1, prob = c(elo_norm-0.1*elo_norm, 0.1*elo_norm+0.1*(1-elo_norm), (1-elo_norm)-0.1*(1-elo_norm)))
    
    ## Transformations to results (accounting for aborts)
    result_1<-ifelse(is.na(result),result_prov,99)
    result_2<-ifelse(result_1==99,99,1-result_1)
    
    ##We randomly generate trash talk
    trash_talk<-sample(0:1,1,prob=c(0.90,0.1))
    
    ##Store the details of the game
    provisional_data_1<-data.frame(id_rival= players[2], result = result_1, trash_talk = trash_talk)
    profiles[[players[1]]][[2]]<-rbind(profiles[[players[1]]][[2]],provisional_data_1)
    
    provisional_data_2<-data.frame(id_rival= players[1], result = result_2, trash_talk = trash_talk)
    profiles[[players[2]]][[2]]<-rbind(profiles[[players[2]]][[2]],provisional_data_2)
    
  }
    
  
  
 
