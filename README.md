// # TrippleX
// Project from the course https://www.udemy.com/course/unrealcourse/


#include <iostream>
#include <ctime>

void PrintIntroduction(int Difficulty)
// välkomstmeddelande som visas på terminalen
{
    std::cout << "\n\nYou come by an old witches hut. Before you knock on the door a hissing voice says:\n";
    std::cout << "For your " << Difficulty;
    std::cout << " task find me this code, or your stay is no more...\n\n";

}

bool PlayGame(int Difficulty)

{    
    PrintIntroduction(Difficulty);
     

    // Deklarera kod
    const int CodeA = rand() % Difficulty + Difficulty;
    const int CodeB = rand() % Difficulty + Difficulty;
    const int CodeC = rand() % Difficulty + Difficulty;

    const int CodeSum = CodeA + CodeB + CodeC;
    const int CodeProduct = CodeA * CodeB * CodeC;

    
    std::cout << "+There are 3 nr in the code";
    std::cout << "\n+The code add-up to: " << CodeSum;
    std::cout << "\n+The codes multiply to give: " <<CodeProduct << std::endl;

// Store player input
    int GuessA, GuessB, GuessC;
    std::cin >> GuessA >> GuessB >> GuessC;
   
    

    int GuessSum = GuessA + GuessB + GuessC;
    int GuessProduct = GuessA * GuessB * GuessC;

    //Check if player guess is correct
    if (GuessSum == CodeSum && GuessProduct == CodeProduct) 
    {
        std::cout << "\nWell done! You may enter my sisters realm ";
        return true;
    }
   else 
   {
       std::cout << "\nWrong my dear, you shall be a nice second breakfast *Glurp* ";
       return false;
   }
}

int main()
{
    srand(time(NULL));
    int LevelDificulty = 1;
    const int MaxLevel = 5;

    while (LevelDificulty <= MaxLevel) // loop game til all lvl are completed
    {
        bool bLevelComplete = PlayGame(LevelDificulty);
        std::cin.clear();
        std::cin.ignore();

        if (bLevelComplete)
        {
            ++LevelDificulty;
        }
        
    }
    std::cout << "\nYou enter the final door. All witches seems pleased with your tasks and have orderd a feast...\nNot of you, but for you!";
     return 0;
}
