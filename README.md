# Capstone
 
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
The aim of this project is to build a model that detects if a player is utilizing performance enhancing software in Call of Duty. The returned handles labeled as 'cheaters' will then be inspected by game administrators for further action.
 
## Data
Player handles were scraped from public and globally ranked Call of Duty Leaderboards found on https://codstats.net/leaderboards/. Player handles from the front, middle, and end of the leaderboards were collected. General statistics and recent match data were obtained for each player. 
   
## Methods
Binarized labels were assigned to each player based on their statistics. If a player was above 3.5 standard deviations above all other players in their ranke in three or more statistics, they were labeled as using performance enhancing software. The data was then over and under sampled to ensure proper class balances. 
    
## EDA Results Notable Features
### General Statistics

#### KDA Ratio vs Average Score Per Game
-KDA and Average Score per Game pic-

Outshine all other players in KDA Ratio and Score per Game

#### Percentage of Wins vs Average Lifetime
-Percentage of Wins vs Average Lifetime pic-

Surprisingly, cheaters don't have a longer than average lifetime span when compared to other players. They are above the norm for percentage of wins    
 
### Match Statistics
 
 #### Shot Count vs Accuracy
 -Shot Count vs Accuracy pic -
 
 Preformance Enhancing software users still have an unusually high accuracy with the highest shot counts out of all players. This combined with the average lifetime indicates an aggressive play style.
 
 #### Hit Count vs Headshot Count
  -Hit Count vs Headshot Count-
  
  A higher proportion of hits for PES users are headshots which indicates unusually high ~precision accuracy~
  

## Modeling Results
  
    
## Conclusions


    
## Repositroy Structure
```
├── images                                
├── data_scripts
    └── web_scraping.ipynb
    └── data_preparation.ipynb
    └── EDA.ipynb
├── modeling_scripts                         
    └── modeling_functions.ipynb
    └── dummy_and_logistic_regression.ipynb                
    └── result_summary.ipynb                   
├── Presentation.pdf                      
└── README.md                           
