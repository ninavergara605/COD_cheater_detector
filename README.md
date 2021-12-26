
# COD Cheater Detector
 
**Author**: *Nina Vergara*
  
## Overview
- [Purpose](#Purpose)
- [Data](#Data)
- [Methods](#Methods)
- [EDA Results: Notable Features](#EDA-Results-Notable-Features) 
- [Modeling Results](#Modeling-Results)
- [Conclusions](#Conclusions)
- [Repository Structure](#Repositroy-Structure)
  

## Purpose
The aim of this project is to build a model that detects if a player is cheating in Call of Duty (COD). Player's are considered cheating if they are playing below their skill level or they are utlizing performance enhancing software. Those that will be labeled as cheaters will then be inspected by game administrators for further action.
 
## Data
Player handles were scraped from public and globally ranked Call of Duty Leaderboards found on https://codstats.net/leaderboards/. Player handles from the front, middle, and end of the leaderboards were collected. General statistics and recent match data were obtained for each player. More than 60,000 records were collected.
   
## Methods
### Hacker Detection
#### Software Descriptions

Two types of performancing enhancing software was considered for this project: Aiming-bots and 'fluid wall' programs. Aiming bots automatically lock weapon sites onto other players. This would dramatically increase the precision of a player's shot. This modification would also simulate a fast reaction time, allowing a player to have a substantially larger number of hits within a short amount of time. Fluid wall programs enable an individual to see player locations through walls and buildings. These programs can also change the color of oppenent tags to indicate if the'yre within shooting distance. This allows a competitive advantage by enabling one to plan and evade ambushes, as well as increasing the accuracy of shots.

#### Hacker Labeling Method

In theory, hackers should outshine other players in the following categories:
* Number of Headshots Per Match
* Match Accuracy
* Number of Hits per Match
* Time Alive per Match

If a player scored 3.5 standard deviations above all other players in 3 of the above categories, an individual was labeled a hacker. 3.5 is a standard threshold for detecting outliers.

### Smurf Detection
#### Smurf Description

A smurf is a seasoned player that disguises themselves as a novice in order to verse others below their skill level. 

#### Smurf Detection

In order to detect a smurf, an individual's play level needs to be compared to their account level. To determine an individuals play level, characteristics that are important in COD's Skill based Match Making (SMM) system were scaled and summed for each player to create a skill score. 

If a players kill score was above the 75th percentile, their play level was 'above average', if a player fell between the 25th and 75th percentile, their play level was 'average', and if players fell below the 25th percentile,  their play level was 'below average'.

A low account level player is one that has a COD rank below 55 (out of 155). If an individual has a low account level, but has an 'above average' play level, they were labeled a smurf.
    
## EDA Results Notable Features
### Hacker Results
#### Match Performance
![image](https://github.com/ninavergara605/capstone/blob/a2b5375d2fef289c302bf846ebf56f411526c730/images/hacker_match_performance.png)

Even though hackers are alive for the same amount of time as regular players, they shoot at a higher pace and they rack in more headshots.

#### Overall Performance
![image](https://github.com/ninavergara605/capstone/blob/a2b5375d2fef289c302bf846ebf56f411526c730/images/hacker_overall_performance.png)

When taking into account overall performance, there's less discrepency between hackers and non-hackers in accuracy and headshots. This suggests that hackers have a history of underperformance in these areas. It would be interesting to see if KDA Ratio and Avg score characteristics are easily skewed by recent performance enhancements for the hackers.

### Smurf Results
#### Match Headshot Count
![image](https://github.com/ninavergara605/capstone/blob/a2b5375d2fef289c302bf846ebf56f411526c730/images/smurf_headshot_count.png)

Smurfs had greater precision when compared to players that were labeled as non-cheaters.

#### Score Per Minute
![image](https://github.com/ninavergara605/capstone/blob/a2b5375d2fef289c302bf846ebf56f411526c730/images/smurf_score_per_minute.png)

Smurfs regularly scored more per game than true players.

#### Average Lifetime
![image](https://github.com/ninavergara605/capstone/blob/a2b5375d2fef289c302bf846ebf56f411526c730/images/smurf_Time_alive.png)

Across all COD levels, players who were labeled as smurfs stayed alive for longer periods of time when compared to true players.

## Modeling Results
Accuracy was chosen as the evaluation metric for modeling. This is to strike a balance between incorrectly banning a professional streamer while correctly banning an individual who is disrupting gameplay for everyone else.

After optimization, the following accuracies were obtained:


![image](https://github.com/ninavergara605/capstone/blob/1be239f29b95dfe2f92c819e136d3d052fc4c45d/images/final_model_preformance.png)

## Conclusions
The RandomForest or Decision tree models offer the highest test accuracy.
    
## Repositroy Structure
```
	
├── images                                
├── data_scripts
    └── web_scraping.ipynb
    └── data_preparation.ipynb
    └── EDA.ipynb
├── modeling_scripts                         
    └── modeling_functions.ipynb
    └── dummy_and_logistic_regression.ipynb                
    └── results.ipynb                   
├── Presentation.pdf                      
└── README.md                           
