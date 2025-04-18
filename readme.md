# Introduction
 - Hello, this is our cooperative program by REESE
 - This is a fighting platformer in pycharm

# Page of references
 - This program is built with the PYGAME library which helps with the development of GUI applications, typically games
 - pixilart.com is a site which provides tools to create pixel art
 - Fonts used are Freesansbold.ttf and Agdasima.ttf

# Other words
 - This game uses game states which determine what part of the code can be run and is ran depending on states rather than storing parts of the game loop into functions
 - The display is updated every game loop rather than individually when there is a change as changes could be lost track of and can cause visual defects although this means it could be less efficient
 - All variables use PascalCase except class subroutine names and class variable names which will be in camelCase
---

# Flow of game for user
 - Pop into menu
 - Character selection
 - Map selection
 - Load into map and countdown
 - Fight until health depleted
 - Restart or quit game

# Section of each program
## Main Program
 - Initialises and loads all required variables and assets
 - Runs a game loop which goes through different blocks of code depending on the game state
    - Menu - Has a series of buttons which leads the user through the program such as to set up the game
    - Character selection - Characters are shown on screen and users can scroll through and select their chosen character
    - Map selection - Maps are shown on screen and users can scroll through ans select their chosen character
    - Game - Players and map is loaded onto the screen and the users can interact with the sprites until either falls below a HP threshold, a prompt then brings users to restart or quit the game

## Font Gen
 - A class which takes attributes of the font, it combines it to create the font
 - Render - Adds the font to the screen
 - Change position - Values are provided to change the position of the font

--- 
# Order of files
```mermaid
---
title : Flow of program files
---
graph TD;
    %% Each main element of the program
    MainScript("All scenes and game is in here")
    UIScript[["Creates Button and Fonts"]]
    SpriteScript[["Creates sprites with attributes and methods"]]

    %% Groups different parts of the program together
    subgraph "Main Program"
        MainScript
        end
    subgraph "UIScript : "
        UIScript
        end
    subgraph "SpriteScript :"
        SpriteScript
        end
    
    %% I cannot figure out how to reorganise this diagram to be more accurate but this shall suffice
    UIScript & SpriteScript --> MainScript
```
```mermaid
---
title : Menu screens
---
graph LR;
    MenuScript("Menu scenes")
    GameScript("Quits and calls Game Script")
    %% Section of main menu
    Play[Enters next stage of game]
    Settings["Settings page"]
    Exit["Exit : Quits the program"]
    %% Character selection
    CharSelection[["Both players have to chose a character before continuing"]]
    Char1; Char2; Char3; Char4
    %% Map selection
    MapSelection[["A player selects the map to play in"]]
    Map1; Map2; Map3; Map4

    %% Groups similar components for organisation
    subgraph "Main menu"
        Play
        Settings
        Exit
        end
    subgraph "Char select"
        Char1 & Char2 & Char3 & Char4
        end
    subgraph "Map select"
        Map1 & Map2 & Map3 & Map4
        end

    MenuScript --> Play & Settings & Exit
    Play --> CharSelection --> Char1 & Char2 & Char3 & Char4 --> MapSelection --> Map1 & Map2 & Map3 & Map4 --> GameEvent
```

# Sprites to draw : 
 - Scenes : Plain match background, Beach, Forest, Hell
 - Sprites : 3 characters based on colour with different variants (Still, hit, kick, heal, move (forward (image will be reversed for backwards), jump, crouch)
 - Effects : Physical hit, ground particle (different according to map), heal effect, low health effect, text effects (sparkle, confetti)
 - Objects/Others : Text Background(Scroll, Paper in gold frame), others...to be thought and implemented of

# To do list : 
 - Get game states working
    - [x] Each game state carries out scenes correctly : display scene and objects, moves on when appropriate 
 - Finish character classes
    - [ ] Get all movement physics working
    - [ ] Character changes sprite under certain actions and can change back automatically
    - [ ] Get character hit boxes working
 - Additional features : 
    - [ ] Sound
       - [ ] Event activated sounds
       - ---[ ] Dynamic sounds based on environment--- not very applicable in most situations
    - [ ] Settings (Keybinds, display size, game values)
    - [ ] Tutorial (custom gamemodes which teaches user or allows user to train)
    - [ ] More sprite actions
       - [ ] Attacks - Slide, types of kicks and punches, etc
       - [ ] Movements - Sprite exclusive movements (higher jumps, faster movement)
    - [ ] More assets - Maps, characters and animations, skins, etc
    - [ ] Saving data (recording match details, done by using JSON files)
    - [ ] Gamemodes (tournament, custom map creation, etc)
    - [ ] Additional objects
    - [ ] Custom maps - Has custom game mechanics with different objects which allows more interaction
    - [ ] Easter eggs (Stuff included in images/animations/comments/console prints)
