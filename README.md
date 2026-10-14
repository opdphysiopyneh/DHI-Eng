# DHI-Eng

<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Pamela Youde Nethersole Eastern Hospital Physiotherapy Department - Dizziness Handicap Inventory (DHI)</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0, shrink-to-fit=no, viewport-fit=cover">
  <style>
    :root {
      --primary: #007AFF;
      --primary-active: #0056b3;
      --bg: #F2F2F7;
      --card-bg: #FFFFFF;
      --text-main: #000000;
      --text-muted: #6C6C70;
      --border: #D1D1D6;
      --selected-bg: #E3F0FF;
      --error-border: #FF3B30;
      --error-bg: #FFF2F2;
    }

    * {
      box-sizing: border-box;
      -webkit-tap-highlight-color: transparent;
      -webkit-text-size-adjust: 100%;
    }

    html, body {
      width: 100%;
      overflow-x: hidden;
      scroll-behavior: smooth;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, "SF Pro Text", "SF Pro Display", "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
      background-color: var(--bg);
      color: var(--text-main);
      margin: 0;
      padding: env(safe-area-inset-top, 12px) 14px calc(36px + env(safe-area-inset-bottom, 20px)) 14px;
      font-size: clamp(17px, 4.8vw, 20px);
      line-height: 1.45;
    }

    .container {
      width: 100%;
      max-width: 600px;
      margin: 0 auto;
    }

    .header-card {
      background: var(--card-bg);
      border-radius: 16px;
      padding: 16px 14px;
      margin-top: 6px;
      margin-bottom: 14px;
      text-align: center;
      box-shadow: 0 1px 4px rgba(0,0,0,0.06);
      border: 1px solid var(--border);
    }

    .hospital-title {
      font-size: clamp(0.95rem, 3.8vw, 1.1rem);
      color: #636366;
      font-weight: 600;
      margin-bottom: 4px;
      line-height: 1.4;
    }

    .main-title {
      font-size: clamp(1.4rem, 5.5vw, 1.85rem);
      font-weight: 800;
      margin: 0 0 8px 0;
      color: var(--text-main);
      line-height: 1.25;
    }

    .instruction {
      font-size: clamp(1.05rem, 4.2vw, 1.2rem);
      color: var(--text-muted);
      margin: 0;
      line-height: 1.5;
    }

    /* Slider Cards */
    .slider-card {
      background: var(--card-bg);
      border-radius: 16px;
      padding: 18px 14px;
      margin-bottom: 14px;
      box-shadow: 0 1px 4px rgba(0,0,0,0.05);
      border: 1.5px solid var(--border);
    }

    .slider-header {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      margin-bottom: 8px;
    }

    .slider-badge {
      font-size: 1.6rem;
      font-weight: 800;
      color: var(--primary);
    }

    .optional-tag {
      font-size: 0.9rem;
      color: #C66900;
      background: #FFF3D6;
      padding: 3px 10px;
      border-radius: 12px;
      font-weight: 700;
      margin-left: 8px;
    }

    .slider-container {
      margin: 20px 0 10px 0;
    }

    .custom-slider {
      -webkit-appearance: none;
      width: 100%;
      height: 10px;
      border-radius: 5px;
      outline: none;
      cursor: pointer;
    }

    .nrs-gradient {
      background: linear-gradient(to right, #34C759 0%, #FFCC00 50%, #FF3B30 100%);
    }

    .groc-gradient {
      background: linear-gradient(to right, #FF3B30 0%, #FFCC00 50%, #34C759 100%);
    }

    .custom-slider::-webkit-slider-thumb {
      -webkit-appearance: none;
      appearance: none;
      width: 28px;
      height: 28px;
      border-radius: 50%;
      background: #FFFFFF;
      border: 3px solid var(--primary);
      box-shadow: 0 2px 6px rgba(0,0,0,0.3);
      cursor: pointer;
      transition: transform 0.1s;
    }

    .custom-slider::-webkit-slider-thumb:active {
      transform: scale(1.15);
    }

    .slider-labels {
      display: flex;
      justify-content: space-between;
      margin-top: 10px;
      font-size: 0.95rem;
      font-weight: 700;
    }

    .label-left {
      color: #28A745;
      text-align: left;
    }

    .label-right {
      color: #DC3545;
      text-align: right;
    }

    .label-center {
      color: var(--text-muted);
      text-align: center;
    }

    .clear-btn {
      width: 100%;
      margin-top: 10px;
      padding: 12px;
      font-size: 1rem;
      background: #E5E5EA;
      color: #1C1C1E;
      border: none;
      border-radius: 12px;
      font-weight: 700;
      cursor: pointer;
      transition: background 0.15s;
    }

    .clear-btn:active {
      background: #D1D1D6;
    }

    /* Question Cards */
    .question-card {
      background: var(--card-bg);
      border-radius: 16px;
      padding: 18px 14px;
      margin-bottom: 14px;
      box-shadow: 0 1px 4px rgba(0,0,0,0.05);
      border: 1.5px solid var(--border);
      transition: border-color 0.2s, background-color 0.2s;
    }

    .question-card.highlight-error {
      border-color: var(--error-border) !important;
      background-color: var(--error-bg);
      animation: pulse-border 1.5s infinite;
    }

    @keyframes pulse-border {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.01); }
    }

    .question-title {
      font-size: clamp(1.2rem, 4.8vw, 1.4rem);
      font-weight: 700;
      color: var(--text-main);
      line-height: 1.35;
      margin-bottom: 12px;
    }

    .options-group {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .option-item {
      display: flex;
      align-items: center;
      padding: 14px 14px;
      border-radius: 14px;
      background: #F8F8FA;
      border: 2px solid transparent;
      cursor: pointer;
      font-size: clamp(1.05rem, 4.2vw, 1.2rem);
      color: #1C1C1E;
      transition: all 0.15s ease-in-out;
      user-select: none;
    }

    .option-item:active {
      transform: scale(0.99);
      background: #E5E5EA;
    }

    .option-item.selected {
      background: var(--selected-bg);
      border-color: var(--primary);
      color: #004CB8;
      font-weight: 700;
    }

    .custom-radio {
      width: 24px;
      height: 24px;
      border-radius: 50%;
      border: 2px solid #8E8E93;
      margin-right: 12px;
      flex-shrink: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #FFF;
      transition: border-color 0.15s, background-color 0.15s;
    }

    .option-item.selected .custom-radio {
      border-color: var(--primary);
      background: var(--primary);
    }

    .option-item.selected .custom-radio::after {
      content: "";
      width: 10px;
      height: 10px;
      background: #FFF;
      border-radius: 50%;
    }

    .option-text {
      flex-grow: 1;
      line-height: 1.4;
    }

    .hidden-radio {
      position: absolute;
      opacity: 0;
      pointer-events: none;
    }

    .calc-btn {
      margin-top: 16px;
      padding: 18px;
      width: 100%;
      background: var(--primary);
      color: #FFFFFF;
      font-size: clamp(1.2rem, 5vw, 1.35rem);
      font-weight: 700;
      border: none;
      border-radius: 16px;
      cursor: pointer;
      box-shadow: 0 4px 14px rgba(0, 122, 255, 0.35);
      transition: background 0.15s, transform 0.1s;
    }

    .calc-btn:active {
      background: var(--primary-active);
      transform: scale(0.98);
    }

    /* Modal */
    .modal {
      display: none;
      position: fixed;
      z-index: 999;
      inset: 0;
      background: rgba(0, 0, 0, 0.5);
      backdrop-filter: blur(8px);
      -webkit-backdrop-filter: blur(8px);
      align-items: center;
      justify-content: center;
      padding: 16px;
    }

    .modal-content {
      background: #FFFFFF;
      padding: 24px 18px;
      border-radius: 22px;
      width: 100%;
      max-width: 400px;
      text-align: center;
      box-shadow: 0 12px 36px rgba(0,0,0,0.25);
    }

    .modal-content h2 {
      margin: 0 0 12px 0;
      font-size: 1.6rem;
    }

    .result-block {
      background: #F8F8FA;
      border-radius: 14px;
      padding: 12px;
      margin-bottom: 12px;
    }

    .result-label {
      font-size: 1rem;
      color: var(--text-muted);
      margin: 0 0 4px 0;
    }

    .result-val {
      font-size: 2.2rem;
      font-weight: 800;
      color: var(--primary);
      margin: 0;
    }

    .notice-box {
      background: #FFF9E6;
      border: 1.5px solid #FFD666;
      padding: 14px;
      margin: 16px 0;
      font-size: 1.05rem;
      color: #874D00;
      border-radius: 12px;
      line-height: 1.5;
      font-weight: 700;
    }

    .close-btn {
      width: 100%;
      padding: 16px;
      background: #1C1C1E;
      color: #FFF;
      font-size: 1.2rem;
      font-weight: 700;
      border: none;
      border-radius: 14px;
      cursor: pointer;
    }
  </style>
</head>
<body>

<div class="container">
  <div class="header-card">
    <div class="hospital-title">Hospital Authority Pamela Youde Nethersole Eastern Hospital<br>Physiotherapy Department</div>
    <h1 class="main-title">Dizziness Handicap Inventory<br>(DHI)</h1>
    <p class="instruction">This questionnaire is designed to determine the difficulties you may experience due to dizziness or unsteadiness.<br><strong>Please answer each question with "Yes", "Sometimes", or "No":</strong></p>
  </div>

  <form id="evaluationForm">
    <!-- Dizziness Numeric Rating Scale (NRS 0–10) -->
    <div class="slider-card" id="nrsCard">
      <div class="slider-header">
        <span class="question-title" style="margin-bottom: 0;">Numeric Rating Scale (NRS)</span>
        <span id="nrsValueDisplay" class="slider-badge">0 / 10</span>
      </div>
      <p style="font-size: 0.95rem; color: var(--text-muted); margin: 4px 0 14px 0;">Please rate your level of dizziness according to your situation today:</p>
      
      <div class="slider-container">
        <input type="range" min="0" max="10" value="0" step="1" class="custom-slider nrs-gradient" id="nrsSlider" oninput="updateNrs(this.value)">
      </div>
      
      <div class="slider-labels">
        <span class="label-left">0<br>No Dizziness</span>
        <span class="label-right">10<br>Dizziness as worst as it could be</span>
      </div>
    </div>

    <!-- Numeric Global Rating of Change Scale (NGRCS -10 to +10, Optional) -->
    <div class="slider-card" id="grocCard">
      <div class="slider-header">
        <div>
          <span class="question-title" style="margin-bottom: 0;">Numeric Global Rating of Change Scale (NGRCS)</span>
          <span class="optional-tag">Optional</span>
        </div>
        <span id="grocValueDisplay" class="slider-badge" style="font-size: 1.25rem;">Not Assessed</span>
      </div>
      <p style="font-size: 0.95rem; color: var(--text-muted); margin: 4px 0 14px 0;">Please slide to rate the overall change in your condition (or leave blank if not applicable):</p>
      
      <div class="slider-container">
        <input type="range" min="-10" max="10" value="0" step="1" class="custom-slider groc-gradient" id="grocSlider" oninput="updateGroc(this.value)">
      </div>
      
      <div class="slider-labels">
        <span class="label-left" style="color: #DC3545;">-10<br>Worst change</span>
        <span class="label-center">0<br>No change</span>
        <span class="label-right" style="color: #28A745;">+10<br>Best change</span>
      </div>
      <button type="button" class="clear-btn" onclick="clearGroc()">Skip / Clear Change Scale Selection</button>
    </div>

    <div id="questionsContainer"></div>
    
    <button type="button" class="calc-btn" onclick="submitAssessment()">Calculate Assessment Result</button>
  </form>
</div>

<div id="scoreModal" class="modal" role="dialog" aria-modal="true" aria-labelledby="modalTitle" onclick="handleBackdropClick(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <h2 id="modalTitle">Assessment Result</h2>
    
    <div class="result-block" id="modalNrsBlock">
      <p class="result-label">Today's Dizziness Level (NRS)</p>
      <p id="modalNrsText" class="result-val">0 / 10</p>
    </div>

    <div class="result-block" id="modalGrocBlock" style="display: none;">
      <p class="result-label">Global Rating of Change (NGRCS)</p>
      <p id="modalGrocText" class="result-val" style="font-size: 1.6rem;">0</p>
    </div>

    <div class="result-block">
      <p class="result-label" id="modalScoreTitle">DHI Total Score</p>
      <p id="modalScoreValue" class="result-val">0 / 100</p>
      <p id="modalScoreSubtitle" style="font-size: 0.95rem; margin: 6px 0 0 0; color: var(--text-muted);"></p>
    </div>

    <div class="notice-box">
      Please do not leave this page and present it to your therapist.<br>
      Alternatively, you may take a screenshot.<br>
      Thank you.
    </div>
    
    <button type="button" class="close-btn" onclick="closeModal()">Close</button>
  </div>
</div>

<script>
var standardOptions = [
  { key: "yes", value: 4, label: "Yes" },
  { key: "sometimes", value: 2, label: "Sometimes" },
  { key: "no", value: 0, label: "No" }
];

var items = [
  "Does looking up increase your problem?",
  "Because of your problem, do you feel frustrated?",
  "Because of your problem, do you restrict your travel for business or recreation?",
  "Does walking down the aisle of a supermarket increase your problems?",
  "Because of your problem, do you have difficulty getting into or out of bed?",
  "Does your problem significantly restrict your participation in social activities, such as going out to dinner, going to the movies, dancing, or going to parties?",
  "Because of your problem, do you have difficulty reading?",
  "Does performing more ambitious activities such as sports, dancing, household chores (sweeping or putting dishes away) increase your problems?",
  "Because of your problem, are you afraid to leave your home without having someone accompany you?",
  "Because of your problem have you been embarrassed in front of others?",
  "Do quick movements of your head increase your problem?",
  "Because of your problem, do you avoid heights?",
  "Does turning over in bed increase your problem?",
  "Because of your problem, is it difficult for you to do strenuous homework or yard work?",
  "Because of your problem, are you afraid people may think you are intoxicated?",
  "Because of your problem, is it difficult for you to go for a walk by yourself?",
  "Does walking down a sidewalk increase your problem?",
  "Because of your problem, is it difficult for you to concentrate?",
  "Because of your problem, is it difficult for you to walk around your house in the dark?",
  "Because of your problem, are you afraid to stay home alone?",
  "Because of your problem, do you feel handicapped?",
  "Has the problem placed stress on your relationships with members of your family or friends?",
  "Because of your problem, are you depressed?",
  "Does your problem interfere with your job or household responsibilities?",
  "Does bending over increase your problem?"
];

var grocEngaged = false;

function renderQuestions() {
  var container = document.getElementById("questionsContainer");
  if (!container) return;
  container.innerHTML = "";

  items.forEach(function(titleText, index) {
    var qNum = index + 1;
    var card = document.createElement("div");
    card.className = "question-card";
    card.id = "card-q" + qNum;

    var title = document.createElement("div");
    title.className = "question-title";
    title.textContent = qNum + ". " + titleText;
    card.appendChild(title);

    var optionsGroup = document.createElement("div");
    optionsGroup.className = "options-group";

    standardOptions.forEach(function(opt) {
      var label = document.createElement("label");
      label.className = "option-item";
      label.htmlFor = "q" + qNum + "_" + opt.key;

      var radio = document.createElement("input");
      radio.type = "radio";
      radio.name = "q" + qNum;
      radio.id = "q" + qNum + "_" + opt.key;
      radio.value = opt.value;
      radio.className = "hidden-radio";

      radio.addEventListener("change", function() {
        var siblings = optionsGroup.querySelectorAll(".option-item");
        siblings.forEach(function(el) { el.classList.remove("selected"); });
        if (radio.checked) {
          label.classList.add("selected");
          card.classList.remove("highlight-error");
        }
      });

      var dot = document.createElement("span");
      dot.className = "custom-radio";
      dot.setAttribute("aria-hidden", "true");

      var itemText = document.createElement("span");
      itemText.className = "option-text";
      itemText.textContent = opt.label;

      label.appendChild(radio);
      label.appendChild(dot);
      label.appendChild(itemText);
      optionsGroup.appendChild(label);
    });

    card.appendChild(optionsGroup);
    container.appendChild(card);
  });
}

if (document.readyState === "loading") {
  document.addEventListener("DOMContentLoaded", renderQuestions);
} else {
  renderQuestions();
}

function updateNrs(val) {
  document.getElementById("nrsValueDisplay").textContent = val + " / 10";
}

function updateGroc(val) {
  grocEngaged = true;
  var text = val;
  if (val > 0) text = "+" + val + " (Better)";
  else if (val < 0) text = val + " (Worse)";
  else text = "0 (No change)";

  document.getElementById("grocValueDisplay").textContent = text;
}

function clearGroc() {
  grocEngaged = false;
  document.getElementById("grocSlider").value = 0;
  document.getElementById("grocValueDisplay").textContent = "Not Assessed";
}

function submitAssessment() {
  var unanswered = [];
  document.querySelectorAll(".question-card").forEach(function(c) {
    c.classList.remove("highlight-error");
  });

  for (var i = 1; i <= items.length; i++) {
    if (!document.querySelector('input[name="q' + i + '"]:checked')) {
      unanswered.push(i);
    }
  }

  if (unanswered.length > 0) {
    unanswered.forEach(function(num) {
      var card = document.getElementById("card-q" + num);
      if (card) card.classList.add("highlight-error");
    });

    var firstCard = document.getElementById("card-q" + unanswered[0]);
    if (firstCard) {
      firstCard.scrollIntoView({ behavior: "smooth", block: "center" });
    }
    return;
  }

  var totalScore = 0;
  var count4 = 0;
  var count2 = 0;
  var count0 = 0;

  for (var j = 1; j <= items.length; j++) {
    var selected = document.querySelector('input[name="q' + j + '"]:checked');
    var val = parseInt(selected.value, 10);
    totalScore += val;
    if (val === 4) count4++;
    else if (val === 2) count2++;
    else if (val === 0) count0++;
  }

  var nrsVal = document.getElementById("nrsSlider").value;
  document.getElementById("modalNrsText").textContent = nrsVal + " / 10";

  if (grocEngaged) {
    document.getElementById("modalGrocBlock").style.display = "block";
    var grocVal = document.getElementById("grocSlider").value;
    var grocText = grocVal;
    if (grocVal > 0) grocText = "+" + grocVal + " (Better)";
    else if (grocVal < 0) grocText = grocVal + " (Worse)";
    else grocText = "0 (No change)";
    document.getElementById("modalGrocText").textContent = grocText;
  } else {
    document.getElementById("modalGrocBlock").style.display = "none";
  }

  document.getElementById("modalScoreValue").textContent = totalScore + " / 100";
  document.getElementById("modalScoreSubtitle").innerHTML = 
    "\"Yes\" (4 pts): <strong>" + count4 + "</strong> | \"Sometimes\" (2 pts): <strong>" + count2 + "</strong> | \"No\" (0 pts): <strong>" + count0 + "</strong>";

  var modal = document.getElementById("scoreModal");
  modal.style.display = "flex";
}

function closeModal() {
  document.getElementById("scoreModal").style.display = "none";
}

function handleBackdropClick(e) {
  if (e.target.id === "scoreModal") {
    closeModal();
  }
}

document.addEventListener("keydown", function(e) {
  if (e.key === "Escape") {
    closeModal();
  }
});
</script>

</body>
</html>
