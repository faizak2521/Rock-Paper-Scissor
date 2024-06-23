# Rock-Paper-Scissor
A C++ program that uses overloaded functions and random number generation to simulate a game of rock, paper, scissors between a player and the computer.

```c++

#include "Player.h" // Include the Player header file
#include <iostream> // Include the input-output stream library
#include <random>   // Include the random number generation library
#include <ctime>    // Include the time library
using namespace std; // Use the standard namespace

// Function prototype for winnerStatus
string winnerStatus(const string& playerPlay, const string& computerPlay);


int main(){
    Player computer{}; // Create an object for the computer
    Player userPlay{}; // Create an object for the player

    string playerChoice; // Declare a string for player's choice

    cout << "Welcome to Rock Paper Scissors" << endl; // Print welcome message
    cout << "\nType rock, paper, or scissors: "; // Prompt user to enter choice
    cin >> playerChoice; // Read and store the player's input

    userPlay.setPlay(playerChoice); // Set the player's choice in the Player object

    cout << "\nYou played: " << playerChoice; // Print the player's choice

    default_random_engine engine(static_cast<unsigned int>(time(0))); // Seed random number generator
    uniform_int_distribution<unsigned int> random(1,3); // Define the range for random numbers
    int computerChoice = random(engine); // Generate a random number for computer's choice
    computer.setPlay(computerChoice); // Set the computer's choice in the Player object

    cout << "\nComputer played: " << computer.getStrPlay() << endl; // Print the computer's choice

    cout << "\n" << winnerStatus(userPlay.getStrPlay(), computer.getStrPlay()); // Print result

    return 0; // Success
}


// Function to determine the winner based on player and computer choices
string winnerStatus(const string& playerPlay, const string& computerPlay){
    if (playerPlay == computerPlay) // Check if it's a tie
        return "It's a tie"; // Return tie message
    else if((playerPlay == "rock" && computerPlay == "scissor") || // Check if player wins with rock
            (playerPlay == "paper" && computerPlay == "rock") ||  // Check if player wins with paper
            (playerPlay == "scissor" && computerPlay == "paper" )) // Check if player wins with scissors
        return "Player wins!"; // Return player win message
    else // If none of the above conditions are met
        return "Computer wins!"; // Return computer win message
}

```
