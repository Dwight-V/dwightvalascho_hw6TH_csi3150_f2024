1. Problem statement of the App: A concise summary of less than 150 words outlining what the app is all about.

    The app is a 5 question quiz about web development. It's main focus is on certain CS abbreviations and their extended form. The questions will be about (HTML, CSS, PHP, SQL, XML), and what each stands for. Each question is timed and the player only has 15 seconds to answer each question. Upon finishing the quiz, the results of the quiz are displayed and a message box asks the user if they want to play again or quit.

2. Functional features of the App: written as a bullet list, outline the functional features of the app.

    * Start Quiz Screen
        * Holds a single element; a button labeled "Start Quiz".
    * Rules Popup
        * Title
            * Holds the title of the popup.
        * Main
            * Holds the list of rules for the quiz.
        * Footer
            * Holds the exit and continue buttons. Exit send the user back to the "Start Quiz Screen", continue sends them to "Quiz Popup".
    * Quiz Popup
        * Title
            * Holds the title of the popup, as well as the timer for each question. A progress bar (which matches the timer's countdown), slowly fills up below the title and timer.
        * Main
            * Holds the question and multiple-choice answers for the user to select from. Upon selecting an answer (or time runs out), the correct answer is highlighted. 
        * Footer
            * Holds the current question's index (1 out of 5, 2 out of 5, etc.) and "next question" button. Upon "next question" clicked, the user is presented the next question in the "Quiz Popup". This repeats until no questions are left.
    * Results Popup
        * Has a crown icon, and a title explaining the quiz is over.
        * The user's dynamic quiz results are displayed: how many questions they got correct out of the the total number of questions, with a few words of praise or disappointment. 
        * "Replay quiz" and "quit quiz" buttons are underneath the user's results. Replay sends the user to "Quiz Popup", quit sends them to "Start Quiz Screen".

    3./4. Explanation of the directory structure/setup of the App as present in the code base and how different files are linked and working together. Explanation of the codebase in each of relevant files, which in this case are the index.html, style.css, questions.js, and quizApp.js files. 

    * index.html
        * Links style.css, questions.js, and quizApp.js together. quizApp.js uses questions.js and style.css, and everything is displayed in index.
        * Has 4 immediate children:
            * "start\_btn": eqivalent to "Start Quiz Screen" from above question. 
            * "info\_box": equivalent to "Rules Popup" from above question.
            * "quiz\_box": equivalent to "Quiz Popup" from above question.
            * "result\_box": equivalent to "Results Popup" from above question.
    * style.css:
        * Standard css styling. Imports fonts, uses class hierarchy to specify certain html elements, uses pseudo classes.
        * Only start\_btn from index.html is shown on initial page load. This is done by setting info\_box, quiz\_box, and result\_box's initial opacity to 0. The boxes then act as "popups" by using js to add an additional class to each object, which sets their opacity to 1 (as well as some other properties, such as their z-index).
    * questions.js:
        * Is simply an array of js object which holds the 5 questions used in the app. Js objects use curly brackets {} then key:value pairs within to signify properties. Each object within the array holds a index number, question text, answer text, and options array.
    * quizApp.js:
        * Is the brain of the app. Is used to add dynamic info to the app, such as the progress bar, timer (and countdown), question info (number, text, and choices), total number of questions, highlighting the correct answer,  hiding/showing the "next question" button (should not be shown until correct answer is highlighted), total number of correctly answered questions.
        * These dynamics are done by adding and removing classes from certain elements (yourElement.classList.add/remove), editing the display text of certain HTML tags (yourElement.innerHTML), even creating new divs and adding them to index.html (yourElement.innerHTML).
        * Although complex, the file is modular, with events such as button clicks being either a series of method calls else a one-liner. Methods include startTimer(), showResults(), optionSelected(), etc. Anything that's done more than once should be it's own method.

