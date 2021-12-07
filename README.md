# Application Architecture - The UI Layer - Guess It!
This is the toy app for lesson 5 of the [Android App Development in Kotlin course on Udacity](https://www.udacity.com/course/developing-android-apps-with-kotlin--ud9012).

## Guess It!

Guess It is a word guessing app you can play with one or more friends. To play, hold the device in landscape, facing away from you with your thumbs on the **Skip** and **Got It** buttons. Your friends can then give you clues to help you guess the word. 

If you get the word right, press **Got It**. If you're stuck, press **Skip**. The game runs for a minute and then shows you your score.


## Screenshots

![Screenshot 0](screenshots/screen0.png) ![Screenshot 1](screenshots/screen1.png) ![Screenshot 2](screenshots/screen2.png)

## How to use this repo while taking the course

Each code repository in this class has a chain of commits that looks like this:

![listofcommits](https://d17h27t6h515a5.cloudfront.net/topher/2017/March/58befe2e_listofcommits/listofcommits.png)

These commits show every step you'll take to create the app. Each commit contains instructions for completing the step.

Each commit also has a **branch** associated with it of the same name as the commit message, as seen below:

![branches](https://d17h27t6h515a5.cloudfront.net/topher/2017/April/590390fe_branches-ud855/branches-ud855.png
)
Access all branches from this tab.

![listofbranches](https://d17h27t6h515a5.cloudfront.net/topher/2017/March/58befe76_listofbranches/listofbranches.png
)


![branchesdropdown](https://d17h27t6h515a5.cloudfront.net/topher/2017/April/590391a3_branches-dropdown-ud855/branches-dropdown-ud855.png
)

The branches are also accessible from the drop-down in the "Code" tab.


## Working with the Course Code

Here are the basic steps for working with and completing exercises in the repo.

The basic steps are:

1. Clone the repo.
2. `checkout` the branch corresponding to the step you want to attempt.
3. Find and complete the TODOs.
4. Optionally commit your code changes.
5. Compare your code with the solution.
6. Repeat steps 2-5 until you've gone trough all the steps to complete the toy app.


**Step 1: Clone the repo**

As you go through the course, you'll be instructed to clone the different exercise repositories, so you don't need to set these up now. You can clone a repository from GitHub in a folder of your choice with the command:

```bash
git clone https://github.com/udacity/REPOSITORY_NAME.git
```

**Step 2: Check out the step branch**

As you go through different steps in the code, you'll be told which step you're on, as well as given a link to the corresponding branch.

Check out the branch associated with that step. The command to check out a branch is:

```bash
git checkout BRANCH_NAME
```

**Step 3: Find and complete the TODOs**

Once you've checked out the branch, you'll have the code in the exact state you need. You'll even have TODOs, which are special comments that tell you all the steps you need to complete the exercise. You can navigate to all the TODOs using Android Studio's TODO tool. To open the TODO tool, click the button at the bottom of the screen that says TODO. This will display a list of all comments with TODO in the project. 

We've numbered the TODO steps so you can do them in order:
![todos](https://d17h27t6h515a5.cloudfront.net/topher/2017/March/58bf00e7_todos/todos.png
)

**Step 4: Commit your code changes**

After you've completed the TODOs, you can optionally commit your changes. This will allow you to see the code you wrote whenever you return to the branch. The following git code will add and save **all** your changes.

```bash
git add .
git commit -m "Your commit message"
```

**Step 5: Compare with the solution**

Most exercises will have a list of steps for you to check off in the classroom. Once you've checked these off, you'll see a pop up window with a link to the solution code. Note the **Diff** link after the Solution link:

![solutionwindow](https://d17h27t6h515a5.cloudfront.net/topher/2017/March/58bf00f9_solutionwindow/solutionwindow.png
)

The **Diff** link will take you to a GitHub diff as seen below:
![diff](https://d17h27t6h515a5.cloudfront.net/topher/2017/March/58bf0108_diffsceenshot/diffsceenshot.png
)

All of the code that was added in the solution is in green, and the removed code (which will usually be the TODO comments) is in red. 

You can also diff your local copy of the code with the corresponding branch as you are working on it:

```bash
git diff BRANCH_NAME
```

## Report Issues
Notice any issues with a repository? Please file a GitHub issue in the repository.


## 新增 GameViewModel 並在 GameFragment 初始化
2. GameViewModel: Create the GameViewModel class, extending ViewModel
3. GameViewModel: Add init and override onCleared; Add log statements to both
4. GameFragment: Create and initialize a GameViewModel, using ViewModelProviders;


## 移動 GameFragment 的 code 到 GameViewModel
1. GameFragment: Move over the word, score and wordList variables to the GameViewModel
2. GameFragment: Move over methods resetList, nextWord, onSkip and onCorrect to GameViewModel
3. GameFragment: Move over this initialization (resetList(), nextWord)to the GameViewModel
4. GameViewModel: Update these onclickListeners to refer to call methods in the ViewModel
5. GameFragment: Update these methods to word and score from the ViewModel


## 加入 LiveData
1. GameViewModel: Wrap word and score in MutableLiveData
2. GameViewModel: Change references to score and word to score. 
3. GameViewModel: Initialize score.value to 0
4. GameFragment: Add viewModel.score observed


## 封裝 LiveData 
1. GameViewModel: Make an internal and external version of the word and score
2. GameViewModel: Make a backing property for external version that returns the internal
3. GameViewModel: Use the internal version (the MutableLiveData) of _score and _word in this init block



## 新增結束遊戲事件
1. GameViewModel: Make a properly encapsulated LiveData called eventGameFinish that holds a boolean
2. GameViewModel: Make the function onGameFinishComplete which makes the value of eventGameFinish false
3. GameViewModel: Set eventGameFinish to true, to signify that the game is over
4. GameFragment: Add an observer of eventGameFinish
5. GameViewModel: Make the function onGameFinishComplete which makes the value of eventGame


## 加上倒數計時
1. GameViewModel: Copy the provided companion object with the timer constants
2. GameViewModel: Create a timer field of type CountDownTimer in the GameViewModel
3. GameViewModel: Create a properly encapsulated LiveData for the current time called currentTime
4. GameViewModel: Copy over the CountDownTimer code and then update currentTime and eventGameFinish appropriately as the timer ticks and finishes
5. Update the logic in the nextWord function so that it doesn't end the game
6. Cancel the timer in onCleared
7. Update the UI


## 加上 ViewModelFactory
1. Create the ScoreViewModel class and have it take in an integer constructor parameter called finalScore
2. Copy over ScoreViewModelFactory:
3. In the overridden create method, construct and return an instance of ScoreViewModel, passing in finalScore
4. Create and construct a ScoreViewModelFactory
5. Create ScoreViewModel by using ViewModelProviders.of as usual, except you’ll also pass in your ScoreViewModelFactory
6. Add a LiveData for the score and the play again event
7. Convert ScoreFragment to properly observe and use ScoreViewModel to update the UI


## Add ViewModel to Data Binding
1. Add a GameViewModel data binding variable to GameFragment layout, You should rebuild the code so all of the generated data binding code is regenerated
2. In the GameFragment layout, use the view model variable and data binding to handle clicking
3. Pass the GameViewModel into the data binding
4. Add a ScoreViewModel data binding variable to ScoreFragment layout
5. In the ScoreFragment layout, use the view model variable and data binding to handle clicking
6. Pass the ScoreViewModel into the data binding and remove OnClickListener setup for playAgainButton


## Add LiveData Data Binding
1. For score_text and word_text use the LiveData from GameViewModel to set the text attribute
2. Call binding.setLifecycleOwner to make the data binding lifecycle aware
3. Remove the score and word observers
4. Use the LiveData from ScoreViewModel to set the score_text text attribute
5. Call binding.setLifecycleOwner and remove the score observer.