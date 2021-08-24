# RockPaperScissors test project

You will create a smart contract named `RockPaperScissors` whereby:  
Alice and Bob can play the classic game of rock, paper, scissors using ERC20 (of your choosing).    
  
- To enroll, each player needs to deposit the right token amount, possibly zero.  
- To play, each Bob and Alice need to submit their unique move.  
- The contract decides and rewards the winner with all token wagered.  

There are many ways to implement this, so we leave that up to you.  
  
## Stretch Goals
Nice to have, but not necessary.
- Make it a utility whereby any 2 people can decide to play against each other.  
- Reduce gas costs as much as possible.
- Let players bet their previous winnings.  
- How can you entice players to play, knowing that they may have their funds stuck in the contract if they face an uncooperative player?  
- Include any tests using Hardhat.

## General Introduction

# There are two type of players in this game:
- PlayerOne: This player creates a Round and also set the playerTwo's address. After that's done the challenger can make his move which element he will choose for the specific round
- PlayerTwo: This player is the challenged person, whom also needs to make his move 
- After both players have chosen their element ( Rock, Paper or Scissor ) the winner gets the bet tokenAmount added by both players (or in case of the draw both players will get their money back).

## Functions

# addBalance

- Pretty Simple, this function can add more tokens to the msg.sender's address

# CreateRound

- With this the msg.sender ( Challenger ) can create a round, every struct element will be pushed to the array, also the challenger needs to bet the value he wants to play with(can be 0 also)


# PlayAsChallenged

- This is the same thing, just for the challenged's address. Also here we check if the round was cancelled already or not, because if it was, then it's no longer possible to play for that specific round

# cancelRound

- This is where the challenger can decide if he no longer wants to play or another possible scenario can be if the challenged never make his move and the money is stuck in the array. He can take it back this way

# _calculateResults

- This is the private function which actually decides who is the winner for the specific round or in case of a draw both players get their money back

# _enrollAsChallenged

- Another Private function which enrolls the challenged as he needs to set up the same amount of token as the challenger did, otherwise he cannot play (except if the value set is 0)

# SortFinished games

- If somebody decides that he or she no longer wants to see which id's belonged to him/her in previous matches, this function deletes the already finished matches (for the msg.sender).

# getRoundById

- A view function with which you can see the status of a roundId

# getAllRoundByOwner

- With this, you can check which Id's belong to the selected address on this function

# getBalance

- A function where you can check the msg.sender's tokenBalance

# _mint

- This function executes when the contract is deployed by the msg.sender. It also mints a 100 Tokens from ERC 20. 

# Progress on stretch Goals

- Make it a utility whereby any 2 people can decide to play against each other => ✔️
- Reduce gas costs as much as possible => not sure on this one, I can remove some events to make less gas usage for an instance. => I believe I know how to implement this now, coming laterz.
- Let players bet their previous winnings => In progress. ✔️
- How can you entice players to play, knowing that they may have their funds stuck in the contract if they face an uncooperative player? => Created the cancelRound function for this ✔️ . But I do not know if it makes the contract any safer.
