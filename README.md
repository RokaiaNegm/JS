1 _ Personalized Welcome Message
function welcomeUser() {
    let name = prompt("Enter your name:");
    let message = name ? `Welcome, ${name}! 😊`: "Welcome, Dear to our world! 😊";
    alert(message);
}

// Call the function
welcomeUser();

2_Character count checker
// Create HTML elements dynamically
document.body.innerHTML = `
    <h2>Character Count Checker</h2>
    <textarea id="textInput" rows="5" cols="30" placeholder="Type something..."></textarea>
    <p>Character Count: <span id="charCount">0</span></p>
`;


let textInput = document.getElementById("textInput");
let charCount = document.getElementById("charCount");

// Update character count on input
textInput.addEventListener("input", function() {
    charCount.innerText = textInput.value.length;
});
![image](https://github.com/user-attachments/assets/694c23cc-8b56-4703-8b95-40ab0a9b7619)

3_//inner Html
document.body.innerHTML = `
    <h2>Age Calculator</h2>
    <label>Enter your birth year:</label>
    <input type="number" id="birthYear" placeholder="e.g. 2002">
    <button onclick="calculateAge()">Calculate Age</button>
    <p id="result"></p>
`;

// Function to calculate age
function calculateAge() {
    let birthYear = document.getElementById("birthYear").value;
    let currentYear = new Date().getFullYear();

    if (birthYear && birthYear > 0 && birthYear <= currentYear) {
        const age = currentYear - birthYear;
        document.getElementById("result").innerText = `You are ${age} years old.`;
    } else {
        document.getElementById("result").innerText = "Please enter a valid birth year.";
    }
}
![image](https://github.com/user-attachments/assets/0d28e699-e73d-403f-a543-5ad3de09c0fc)

4_String Case Manipulator (Uppercase & Lowercase)
document.body.innerHTML = `
    <h2>String Case Manipulator</h2>
    <input type="text" id="textInput" placeholder="Enter text here">
    <button onclick="toUpperCase()">UPPERCASE</button>
    <button onclick="toLowerCase()">lowercase</button>
    <p>Result: <span id="result"></span></p>
`;

// Function to convert text to uppercase
function toUpperCase() {
    let text = document.getElementById("textInput").value;
    document.getElementById("result").innerText = text.toUpperCase();
}

// Function to convert text to lowercase
function toLowerCase() {
    let text = document.getElementById("textInput").value;
    document.getElementById("result").innerText = text.toLowerCase();
}
![image](https://github.com/user-attachments/assets/79cef5e0-1d28-4bc9-866f-a62d9fb53485)

5_Word Replacemen
document.body.innerHTML = `
    <h2>Word Replacement Tool</h2>
    <input type="text" id="sentence" placeholder="Enter a sentence"><br><br>
    <input type="text" id="oldWord" placeholder="Word to replace">
    <input type="text" id="newWord" placeholder="New word">
    <button onclick="replaceWord()">Replace</button>
    <p>Updated Sentence: <span id="result"></span></p>
`;

// Function to replace a word in the sentence
function replaceWord() {
    let sentence = document.getElementById("sentence").value;
    let oldWord = document.getElementById("oldWord").value;
    let newWord = document.getElementById("newWord").value;

    if (sentence && oldWord && newWord) {
        let updatedSentence = sentence.replace(new RegExp(oldWord, "gi"), newWord);
        document.getElementById("result").innerText = updatedSentence;
    } else {
        document.getElementById("result").innerText = "Please enter all fields.";
    }
}
![image](https://github.com/user-attachments/assets/db5e9df6-95da-493e-9dc0-0ea6c58c81dc)

6_Number Guessing Game
let randomNumber = Math.floor(Math.random() * 100) + 1;
let attempts = 0;

document.body.innerHTML = `
    <h2>🎯 Number Guessing Game</h2>
    <p>Guess a number between 1 and 100</p>
    <input type="number" id="guessInput" placeholder="Enter your guess">
    <button onclick="checkGuess()">Submit Guess</button>
    <p id="message"></p>
`;

// Function to check the user's guess using switch
function checkGuess() {
    let userGuess = parseInt(document.getElementById("guessInput").value);
    let message = document.getElementById("message");
    attempts++;

    switch (true) {
        case isNaN(userGuess) || userGuess < 1 || userGuess > 100:
            message.innerText = "⚠️ Please enter a valid number between 1 and 100.";
            break;
        case userGuess > randomNumber:
            message.innerText = "📉 Too high! Try again.";
            break;
        case userGuess < randomNumber:
            message.innerText = "📈 Too low! Try again.";
            break;
        case userGuess === randomNumber:
            message.innerText = `🎉 Correct! You guessed it in ${attempts} attempts.`;
            break;
    }
}
![image](https://github.com/user-attachments/assets/e6e4cbf8-810c-4451-ad8b-b89c51b1e352)

7_ Simple Quiz App:
let quizData = [
    {
        question: "What is the output of the following code?\n\nlet add = (a, b) => a + b;\nconsole.log(add(2, 3));",
        options: ["5", '"23"', "undefined", "Error"],
        answer: "5"
    },
    {
        question: "Which language is used for web development?",
        options: ["Python", "JavaScript", "C++", "Java"],
        answer: "JavaScript"
    },
    {
        question: "What will `typeof null` return in JavaScript?",
        options: ["null", "undefined", "object", "string"],
        answer: "object"
    },
    {
        question: "What does the push() method do in JavaScript?",
        options:[" Removes the last element of an array","Adds one or more elements to the end of an array",
                  "Reverses the order of elements in an array","Sorts the elements of an array"],
        answer: "Adds one or more elements to the end of an array"
    }
];

let currentQuestion = 0;
let score = 0;

//  HTML elements 
document.body.innerHTML = `
    <h2>🧠 Simple Quiz App</h2>
    <p id="question"></p>
    <div id="options"></div>
    <button onclick="nextQuestion()">Next</button>
    <p id="score"></p>
`;

// Function to load the quiz question
function loadQuestion() {
    let quiz = quizData[currentQuestion];
    document.getElementById("question").innerText = quiz.question;

    let optionsHTML = "";
    quiz.options.forEach(option => {
        optionsHTML += `<button onclick="checkAnswer('${option}')">${option}</button><br>`;
    });

    document.getElementById("options").innerHTML = optionsHTML;
}

// Function to check the answer
function checkAnswer(selected) {
    if (selected === quizData[currentQuestion].answer) {
        score++;
    }
    document.getElementById("score").innerText = `Score: ${score}`;
}

// Function to load the next question
function nextQuestion() {
    currentQuestion++;
    if (currentQuestion < quizData.length) {
        loadQuestion();
    } else {
        document.body.innerHTML = `<h2>🎉 Quiz Completed!</h2><p>Your Final Score: ${score}</p>`;
    }
}

// Load the first question
loadQuestion();


![image](https://github.com/user-attachments/assets/2ed13ae3-4bca-42d6-8bff-b557bb7378d5)




