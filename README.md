# hci h


<!DOCTYPE html>
    <html>
        <head>
            <title> Quiz System </title>
            <link rel="stylesheet" href="style.css">
        </head>
    <body>
        <div class="app">
            <h1> Quiz System </h1>
            <div class = "quiz">
                <h2 id="question">Select Quiz </h2>
                <div id = "answer-buttons">
                    <a href="math.html">
                        <button class="btn">Math Quiz</button>
                    </a>
                    <a href="science.html">
                        <button class="btn">Science Quiz</button>
                    </a>
                    <a href="english.html">
                        <button class="btn">English Quiz</button>
                    
                    </a>
                    <a href="filipino.html">
                        <button class="btn">Filipino Quiz</button>
                    
                    </a>
                </div>
                <button id="next-button">Next</button>
            </div>
            
        </div>
    </body>
    </html>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Science Quiz</title>
  <link rel="stylesheet" href="styles.css" />
  <style>
    .correct {
      background-color: lightgreen;
    }
    .wrong {
      background-color: lightcoral;
    }
    .timer-display {
      font-size: 18px;
      color: #333;
      margin-bottom: 20px;
    }
    .question {
      margin-bottom: 15px;
    }
    .bottom-button {
      margin-top: 20px;
    }
    #result {
      margin-top: 20px;
      font-size: 18px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Science Quiz</h1>
    <div id="timer" class="timer-display">Time: 60</div>
    <form id="scienceQuiz">
      <div class="question">
        <p>1. What is the chemical symbol for water?</p>
        <label><input type="radio" name="q1" value="a" /> O<sub>2</sub></label>
        <label><input type="radio" name="q1" value="b" /> H<sub>2</sub>O</label>
        <label><input type="radio" name="q1" value="c" /> CO<sub>2</sub></label>
      </div>
      <div class="question">
        <p>2. What is the largest planet in our solar system?</p>
        <label><input type="radio" name="q2" value="a" /> Earth</label>
        <label><input type="radio" name="q2" value="b" /> Jupiter</label>
        <label><input type="radio" name="q2" value="c" /> Saturn</label>
      </div>
      <div class="question">
        <p>3. What is the boiling point of water?</p>
        <label><input type="radio" name="q3" value="a" /> 50°C</label>
        <label><input type="radio" name="q3" value="b" /> 100°C</label>
        <label><input type="radio" name="q3" value="c" /> 200°C</label>
      </div>
      <div class="question">
        <p>4. What is the powerhouse of the cell?</p>
        <label><input type="radio" name="q4" value="a" /> Nucleus</label>
        <label><input type="radio" name="q4" value="b" /> Mitochondria</label>
        <label><input type="radio" name="q4" value="c" /> Ribosome</label>
      </div>
      <div class="question">
        <p>5. What element does 'O' represent on the periodic table?</p>
        <label><input type="radio" name="q5" value="a" /> Oxygen</label>
        <label><input type="radio" name="q5" value="b" /> Ozone</label>
        <label><input type="radio" name="q5" value="c" /> Osmium</label>
      </div>

      <div id="result"></div>

      <button type="button" id="submitBtn" onclick="checkAnswers()">Submit</button>

      <div class="bottom-button">
        <a href="index.html" id="takeOtherQuizBtn" onclick="preventNavigation(event)">TAKE OTHER QUIZ</a>
      </div>
    </form>
  </div>

  <script>
    let timeLeft = 60;
    let timerInterval;
    let timerStarted = false;

    function disableInputs() {
      document.querySelectorAll('input[type="radio"]').forEach(input => input.disabled = true);
    }

    function disableAfterSubmission() {
      document.getElementById('submitBtn').disabled = true;
      disableInputs();
    }

    function stopTimer() {
      clearInterval(timerInterval);
    }

    function updateTimer() {
      const timerDisplay = document.getElementById('timer');
      timerDisplay.textContent = 'Time: ' + timeLeft;

      if (timeLeft <= 0) {
        clearInterval(timerInterval);
        alert("Time's up!");
        disableInputs();
        disableAfterSubmission();
        checkAnswers();
        enableTakeOtherQuizBtn(); // Allow the user to take another quiz after time is up
      } else {
        timeLeft--;
      }
    }

    function startTimer() {
      timerInterval = setInterval(updateTimer, 1000);
    }

    function startQuizTimer() {
      if (!timerStarted) {
        startTimer();
        timerStarted = true;
      }
    }

    document.querySelectorAll('input[type="radio"]').forEach(button => {
      button.addEventListener('click', startQuizTimer);
    });

    function preventNavigation(event) {
      const answered = document.querySelectorAll('input[type="radio"]:checked').length;
      if (answered < 5) {
        event.preventDefault();
        alert("Please answer all questions before switching quizzes.");
      }
    }

    function enableTakeOtherQuizBtn() {
      const takeOtherQuizBtn = document.getElementById('takeOtherQuizBtn');
      takeOtherQuizBtn.removeAttribute('onclick');
      takeOtherQuizBtn.style.pointerEvents = 'auto';

      
    }

    function checkAnswers() {
      const correctAnswers = {
        q1: 'b', // H2O
        q2: 'b', // Jupiter
        q3: 'b', // 100°C
        q4: 'b', // Mitochondria
        q5: 'a'  // Oxygen
      };

      let total = 5;
      let score = 0;
      let unanswered = [];

      // Clear old highlights
      document.querySelectorAll('label').forEach(label => {
        label.classList.remove('correct', 'wrong');
      });

      // Check if all questions are answered
      for (let question in correctAnswers) {
        const selected = document.querySelector(`input[name="${question}"]:checked`);
        if (!selected) {
    
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>English Quiz</title>
  <link rel="stylesheet" href="styles.css" />
  <style>
    .correct {
      background-color: lightgreen;
    }
    .wrong {
      background-color: lightcoral;
    }
    .timer-display {
      font-size: 18px;
      color: #333;
      margin-bottom: 20px;
    }
    .question {
      margin-bottom: 15px;
    }
    .bottom-button {
      margin-top: 20px;
    }
    #result {
      margin-top: 20px;
      font-size: 18px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>English Quiz</h1>
    <div id="timer" class="timer-display">Time: 60</div>
    <form id="englishQuiz">
      <div class="question">
        <p>1. Which of the following is a synonym for "happy"?</p>
        <label><input type="radio" name="q1" value="a" /> Sad</label>
        <label><input type="radio" name="q1" value="b" /> Joyful</label>
        <label><input type="radio" name="q1" value="c" /> Angry</label>
      </div>
      <div class="question">
        <p>2. What is the plural form of "child"?</p>
        <label><input type="radio" name="q2" value="a" /> Childs</label>
        <label><input type="radio" name="q2" value="b" /> Children</label>
        <label><input type="radio" name="q2" value="c" /> Childes</label>
      </div>
      <div class="question">
        <p>3. Choose the correct sentence:</p>
        <label><input type="radio" name="q3" value="a" /> She can sings well.</label>
        <label><input type="radio" name="q3" value="b" /> She can sing well.</label>
        <label><input type="radio" name="q3" value="c" /> She can sung well.</label>
      </div>
      <div class="question">
        <p>4. What is the antonym of "difficult"?</p>
        <label><input type="radio" name="q4" value="a" /> Easy</label>
        <label><input type="radio" name="q4" value="b" /> Hard</label>
        <label><input type="radio" name="q4" value="c" /> Complicated</label>
      </div>
      <div class="question">
        <p>5. Which of the following is a proper noun?</p>
        <label><input type="radio" name="q5" value="a" /> city</label>
        <label><input type="radio" name="q5" value="b" /> John</label>
        <label><input type="radio" name="q5" value="c" /> dog</label>
      </div>

      <div id="result"></div>

      <button type="button" id="submitBtn" onclick="checkAnswers()">Submit</button>

      <div class="bottom-button">
        <a href="index.html" id="takeOtherQuizBtn" onclick="preventNavigation(event)">TAKE OTHER QUIZ</a>
      </div>
    </form>
  </div>

  <script>
    let timeLeft = 60;
    let timerInterval;
    let timerStarted = false;

    function disableInputs() {
      document.querySelectorAll('input[type="radio"]').forEach(input => input.disabled = true);
    }

    function disableAfterSubmission() {
      document.getElementById('submitBtn').disabled = true;
      disableInputs();
    }

    function stopTimer() {
      clearInterval(timerInterval);
    }

    function updateTimer() {
      const timerDisplay = document.getElementById('timer');
      timerDisplay.textContent = 'Time: ' + timeLeft;

      if (timeLeft <= 0) {
        clearInterval(timerInterval);
        alert("Time's up!");
        disableInputs();
        disableAfterSubmission();
        checkAnswers();
        enableTakeOtherQuizBtn();
      } else {
        timeLeft--;
      }
    }

    function startTimer() {
      timerInterval = setInterval(updateTimer, 1000);
    }

    function startQuizTimer() {
      if (!timerStarted) {
        startTimer();
        timerStarted = true;
      }
    }

    document.querySelectorAll('input[type="radio"]').forEach(button => {
      button.addEventListener('click', startQuizTimer);
    });

    function preventNavigation(event) {
      const answered = document.querySelectorAll('input[type="radio"]:checked').length;
      if (answered < 5) {
        event.preventDefault();
        alert("Please answer all questions before switching quizzes.");
      }
    }

    function enableTakeOtherQuizBtn() {
      const takeOtherQuizBtn = document.getElementById('takeOtherQuizBtn');
      takeOtherQuizBtn.removeAttribute('onclick');
      takeOtherQuizBtn.style.pointerEvents = 'auto';
      
    }

    function checkAnswers() {
      const correctAnswers = {
        q1: 'b', // Joyful
        q2: 'b', // Children
        q3: 'b', // She can sing well.
        q4: 'a', // Easy
        q5: 'b'  // John
      };

      let total = 5;
      let score = 0;
      let unanswered = [];

      document.querySelectorAll('label').forEach(label => {
        label.classList.remove('correct', 'wrong');
      });

      for (let question in correctAnswers) {
        const selected = document.querySelector(`input[name="${question}"]:checked`);
        if (!selected) {
          unanswered.push(question);
        }
      }

      if (unanswered.length > 0) {
        const result = document.getElementById("result");

<

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Filipino Quiz</title>
  <link rel="stylesheet" href="styles.css" />
  <style>
    .correct {
      background-color: lightgreen;
    }
    .wrong {
      background-color: lightcoral;
    }
    .timer-display {
      font-size: 18px;
      color: #333;
      margin-bottom: 20px;
    }
    .question {
      margin-bottom: 15px;
    }
    .bottom-button {
      margin-top: 20px;
    }
    #result {
      margin-top: 20px;
      font-size: 18px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Filipino Quiz</h1>
    <div id="timer" class="timer-display">Time: 60</div>
    <form id="filipinoQuiz">
      <div class="question">
        <p>1. Ano ang pambansang wika ng Pilipinas?</p>
        <label><input type="radio" name="q1" value="a" /> Ingles</label>
        <label><input type="radio" name="q1" value="b" /> Cebuano</label>
        <label><input type="radio" name="q1" value="c" /> Filipino</label>
      </div>
      <div class="question">
        <p>2. Sino ang kilalang "Ama ng Balagtasan"?</p>
        <label><input type="radio" name="q2" value="a" /> Francisco Balagtas</label>
        <label><input type="radio" name="q2" value="b" /> Jose Rizal</label>
        <label><input type="radio" name="q2" value="c" /> Lope K. Santos</label>
      </div>
      <div class="question">
        <p>3. Anong bahagi ng pananalita ang naglalarawan sa pangngalan?</p>
        <label><input type="radio" name="q3" value="a" /> Pang-abay</label>
        <label><input type="radio" name="q3" value="b" /> Pang-uri</label>
        <label><input type="radio" name="q3" value="c" /> Pandiwa</label>
      </div>
      <div class="question">
        <p>4. Ano ang tawag sa dalawang salitang pinagsama upang makabuo ng bagong salita?</p>
        <label><input type="radio" name="q4" value="a" /> Tambalan</label>
        <label><input type="radio" name="q4" value="b" /> Inuulit</label>
        <label><input type="radio" name="q4" value="c" /> Payak</label>
      </div>
      <div class="question">
        <p>5. Alin sa mga sumusunod ang isang epiko?</p>
        <label><input type="radio" name="q5" value="a" /> Ibong Adarna</label>
        <label><input type="radio" name="q5" value="b" /> Biag ni Lam-ang</label>
        <label><input type="radio" name="q5" value="c" /> Florante at Laura</label>
      </div>

      <div id="result"></div>

      <button type="button" id="submitBtn" onclick="checkAnswers()">Submit</button>

      <div class="bottom-button">
        <a href="index.html" id="takeOtherQuizBtn" onclick="preventNavigation(event)">TAKE OTHER QUIZ</a>
      </div>
    </form>
  </div>

  <script>
    let timeLeft = 60;
    let timerInterval;
    let timerStarted = false;

    function disableInputs() {
      document.querySelectorAll('input[type="radio"]').forEach(input => input.disabled = true);
    }

    function disableAfterSubmission() {
      document.getElementById('submitBtn').disabled = true;
      disableInputs();
    }

    function stopTimer() {
      clearInterval(timerInterval);
    }

    function updateTimer() {
      const timerDisplay = document.getElementById('timer');
      timerDisplay.textContent = 'Time: ' + timeLeft;

      if (timeLeft <= 0) {
        clearInterval(timerInterval);
        alert("Time's up!");
        disableInputs();
        disableAfterSubmission();
        checkAnswers();
        enableTakeOtherQuizBtn();
      } else {
        timeLeft--;
      }
    }

    function startTimer() {
      timerInterval = setInterval(updateTimer, 1000);
    }

    function startQuizTimer() {
      if (!timerStarted) {
        startTimer();
        timerStarted = true;
      }
    }

    document.querySelectorAll('input[type="radio"]').forEach(button => {
      button.addEventListener('click', startQuizTimer);
    });

    function preventNavigation(event) {
      const answered = document.querySelectorAll('input[type="radio"]:checked').length;
      if (answered < 5) {
        event.preventDefault();
        alert("Sagutin muna ang lahat ng tanong bago lumipat ng quiz.");
      }
    }

    function enableTakeOtherQuizBtn() {
      const takeOtherQuizBtn = document.getElementById('takeOtherQuizBtn');
      takeOtherQuizBtn.removeAttribute('onclick');
      takeOtherQuizBtn.style.pointerEvents = 'auto';

      
    }

    function checkAnswers() {
      const correctAnswers = {
        q1: 'c', // Filipino
        q2: 'a', // Francisco Balagtas
        q3: 'b', // Pang-uri
        q4: 'a', // Tambalan
        q5: 'b'  // Biag ni Lam-ang
      };

      let total = 5;
      let score = 0;
      let unanswered = [];

      document.querySelectorAll('label').forEach(label => {
        label.classList.remove('correct', 'wrong');
      });

      for (let question in correctAnswers) {
        const selected = document.querySelector(`input[name="${question}"]:checked`);
        if (!selected) {
          unanswered.push(question)

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Math Quiz</title>
  <link rel="stylesheet" href="styles.css" />
  <style>
    .correct {
      background-color: lightgreen;
    }
    .wrong {
      background-color: lightcoral;
    }
    .timer-display {
      font-size: 18px;
      color: #333;
      margin-bottom: 20px;
    }
    .question {
      margin-bottom: 15px;
    }
    .bottom-button {
      margin-top: 20px;
    }
    #result {
      margin-top: 20px;
      font-size: 18px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Math Quiz</h1>
    <div id="timer" class="timer-display">Time: 60</div>
    <form id="mathQuiz">
      <div class="question">
        <p>1. What is 5 + 3?</p>
        <label><input type="radio" name="q1" value="a" /> 7</label>
        <label><input type="radio" name="q1" value="b" /> 8</label>
        <label><input type="radio" name="q1" value="c" /> 9</label>
      </div>
      <div class="question">
        <p>2. What is 10 - 4?</p>
        <label><input type="radio" name="q2" value="a" /> 5</label>
        <label><input type="radio" name="q2" value="b" /> 6</label>
        <label><input type="radio" name="q2" value="c" /> 7</label>
      </div>
      <div class="question">
        <p>3. What is 6 × 2?</p>
        <label><input type="radio" name="q3" value="a" /> 10</label>
        <label><input type="radio" name="q3" value="b" /> 12</label>
        <label><input type="radio" name="q3" value="c" /> 14</label>
      </div>
      <div class="question">
        <p>4. What is 12 ÷ 4?</p>
        <label><input type="radio" name="q4" value="a" /> 2</label>
        <label><input type="radio" name="q4" value="b" /> 3</label>
        <label><input type="radio" name="q4" value="c" /> 4</label>
      </div>
      <div class="question">
        <p>5. What is 7 + 6?</p>
        <label><input type="radio" name="q5" value="a" /> 12</label>
        <label><input type="radio" name="q5" value="b" /> 13</label>
        <label><input type="radio" name="q5" value="c" /> 14</label>
      </div>

      <div id="result"></div>

      <button type="button" id="submitBtn" onclick="checkAnswers()">Submit</button>

      <div class="bottom-button">
        <a href="index.html" id="takeOtherQuizBtn" onclick="preventNavigation(event)">TAKE OTHER QUIZ</a>
      </div>
    </form>
  </div>

  <script>
    let timeLeft = 60;
    let timerInterval;
    let timerStarted = false;

    function disableInputs() {
      document.querySelectorAll('input[type="radio"]').forEach(input => input.disabled = true);
    }

    function disableAfterSubmission() {
      document.getElementById('submitBtn').disabled = true;
      disableInputs();
    }

    function stopTimer() {
      clearInterval(timerInterval);
    }

    function updateTimer() {
      const timerDisplay = document.getElementById('timer');
      timerDisplay.textContent = 'Time: ' + timeLeft;

      if (timeLeft <= 0) {
        clearInterval(timerInterval);
        alert("Time's up!");
        disableInputs();
        disableAfterSubmission();
        checkAnswers();
        enableTakeOtherQuizBtn();
      } else {
        timeLeft--;
      }
    }

    function startTimer() {
      timerInterval = setInterval(updateTimer, 1000);
    }

    function startQuizTimer() {
      if (!timerStarted) {
        startTimer();
        timerStarted = true;
      }
    }

    document.querySelectorAll('input[type="radio"]').forEach(button => {
      button.addEventListener('click', startQuizTimer);
    });

    function preventNavigation(event) {
      const answered = document.querySelectorAll('input[type="radio"]:checked').length;
      if (answered < 5) {
        event.preventDefault();
        alert("Please answer all questions before switching quizzes.");
      }
    }

    function enableTakeOtherQuizBtn() {
      const takeOtherQuizBtn = document.getElementById('takeOtherQuizBtn');
      takeOtherQuizBtn.removeAttribute('onclick');
      takeOtherQuizBtn.style.pointerEvents = 'auto';

      
    }

    function checkAnswers() {
      const correctAnswers = {
        q1: 'b', // 8
        q2: 'b', // 6
        q3: 'b', // 12
        q4: 'b', // 3
        q5: 'b'  // 13
      };

      let total = 5;
      let score = 0;
      let unanswered = [];

      document.querySelectorAll('label').forEach(label => {
        label.classList.remove('correct', 'wrong');
      });

      for (let question in correctAnswers) {
        const selected = document.querySelector(`input[name="${question}"]:checked`);
        if (!selected) {
          unanswered.push(question);
        }
      }

      if (unanswered.length > 0) {
        const result = document.getElementById("result");
        result.textContent = "Please answer all the questions before submitting.";
        result.style.color = "red";
        return;
      }

      for (let question in correctAnswers) {
        const selected = document.querySelector(`input[name="${qu


* {
        margin: 0;
        padding: 0;
        font-family: 'Poppins', sans-serif;
        box-sizing: border-box;
    }
    body {
        background-color: #351da0;
    }
    .app {
        background: #ededf0;
        width: 90%;
        max-width: 600px;
        margin: 100px auto 0;
        border-radius: 10px;
        padding: 30px;
    }
    .app h1 {
        text-align: center;
        font-size: 25px;
        color: #351da0;
        font-weight: 600;
        border-bottom: 1px solid #351da0;
        padding-bottom: 10px;
    }
    .quiz{
        margin-top: 20px 0;
    }
    .quiz h2 {
        font-size: 18px;
        color: #351da0;
        font-weight: 600;   
    }
    .btn{
        background-color: #ededf0;
        color: rgb(0, 0, 0);
        font-weight: 500;
        width: 100%;
        border: 1px solid  #351da0;
        padding: 10px;
        margin-top: 20px;
        text-align: left;
        border-radius: 4px;
        cursor: pointer;
        transition: all 0.3s ease;
    }
    .btn:hover{
        background-color: #000000;
        color: #ededf0;
    }
    #next-button{
        background: #351da0;
        color: rgb(252, 247, 247);
        font-weight: 500;
        width: 150px;
        border: 0;
        padding: 10px;
        margin: 20px auto 0;
        border-radius: 4px;
        cursor: pointer;
        display: none;
        
    }

body {
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        margin: 0;
        padding: 0;
        display: flex;
        justify-content: center;
        align-items: flex-start;
        min-height: 100vh;
        background: linear-gradient(135deg, #d0eaff, #f3f9d2);

    }
    .container {
        background:#ffffff;
        padding: 30px 40px;
        margin-top: 50px;
        border-radius: 16px;
        box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
        width: 100%;
        max-width: 600px;
    }
    h1 {
        text-align: center;
        color: #020202;
        font-size: 28px;
        margin-bottom: 25px;
    }

    .question {
        margin-bottom: 25px;
    }

    .question p {
        font-weight: bold;
        margin-bottom: 8px;
        font-size: 18px;
    }

    label {
        display: block;
        margin-bottom: 6px;
        padding: 6px 10px;
        background: #ffffff;
        border-radius: 6px;
        cursor: pointer;
        transition: 0.3s ease;
    }

    label:hover {
        background: #e2e8f0;
    }

    input[type="radio"] {
        margin-right: 10px;
    }

    button {
        background-color: #351da0;
        color: white;
        border: none;
        padding: 12px 24px;
        border-radius: 8px;
        font-size: 16px;
        cursor: pointer;
        transition: background-color 0.3s ease;
        width: 100%;
        margin-top: 10px;
    }
    button:hover {
        background-color: #351da0;
    }
    #result {
        margin-top: 20px;
        font-size: 20px;
        color: #1e293b;
        text-align: center;
        font-weight: bold;
    }
    .bottom-button {
        text-align: center;
        margin-top: 25px;
    }
    
    .bottom-button a {
        display: inline-block;
        background-color: #2c2586;
        color: #fff;
        padding: 10px 18px;
        border-radius: 6px;
        text-decoration: none;
        transition: background-color 0.3s ease;
        font-size: 14px;
    }
    
    .bottom-button a:hover {
        background-color: #07a028;
    }
