# My-First-Project
Discover a versatile web app offering date calculations, currency conversions, mortgage estimates, BMI calculations, loan planning, and calorie tracking. With a sleek design and powerful features, this calculator adapts to your needs, making computations easy and informed decisions a breeze. Your go-to tool for precise calculations.

<!DOCTYPE html>
<html lang="en">
  <head top>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Date Calculator</title>
    <style>
      body {
        background: linear-gradient(
          45deg,
          #ff6b6b,
          #ffa07a,
          #f0e68c,
          #98fb98,
          #6a5acd,
          #ff6b6b
        );
        background-size: 400% 400%;
        animation: gradient 15s ease infinite;
      }

      @keyframes gradient {
        0% {
          background-position: 0% 50%;
        }
        50% {
          background-position: 100% 50%;
        }
        100% {
          background-position: 0% 50%;
        }
      }

      /* Additional styles for your content */
      .content {
        text-align: center;
        padding: 20px;
        color: white;
        font-size: 24px;
        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
      }

      body {
        font-family: Arial, sans-serif;
        background-color: #ffffff;
        margin: 5;
        padding: 10;
      }

      .container {
        max-width: 800px;
        margin: 0 auto;
        padding: 20px;
        text-align: center;
        background-color: #fff;
        border-radius: 10px;
        box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
      }

      h1 {
        color: #007bff;
      }

      label {
        font-weight: bold;
        display: block;
        margin-top: 15px;
      }

      input[type="date"] {
        width: 97%;
        padding: 10px;
        margin: 5px 0;
        border: 2px solid #ccc;
        border-radius: 5px;
        box-shadow: 0 0 5px rgba(0, 0, 0, 0.2);
      }

      button {
        background-color: #007bff;
        color: white;
        border: none;
        padding: 15px 30px;
        margin-top: 15px;
        border-radius: 5px;
        cursor: pointer;
        transition: background-color 0.3s;
      }

      button:hover {
        background-color: #0056b3;
      }

      #result {
        font-weight: bold;
        margin-top: 20px;
      }

      #result p {
        margin-bottom: 5px;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <h1>Date Calculator</h1>
      <label for="startDate">Start Date:</label>
      <input type="date" id="startDate" />

      <label for="endDate">End Date:</label>
      <input type="date" id="endDate" />

      <button onclick="calculateDateDifference()">Calculate</button>

      <div id="result">
        <p>Seconds: <span id="seconds">0.00</span></p>
        <p>Minutes: <span id="minutes">0.00</span></p>
        <p>Hours: <span id="hours">0.00</span></p>
        <p>Days: <span id="days">0.00</span></p>
        <p>Weeks: <span id="weeks">0.00</span></p>
        <p>Months: <span id="months">0</span></p>
        <p>Years: <span id="years">0.00</span></p>
      </div>
    </div>

    <script>
      function calculateDateDifference() {
        const startDate = new Date(document.getElementById("startDate").value);
        const endDate = new Date(document.getElementById("endDate").value);

        if (!isNaN(startDate.getTime()) && !isNaN(endDate.getTime())) {
          const timeDifference = endDate - startDate;
          const millisecondsInSecond = 1000;
          const millisecondsInMinute = millisecondsInSecond * 60;
          const millisecondsInHour = millisecondsInMinute * 60;
          const millisecondsInDay = millisecondsInHour * 24;
          const millisecondsInWeek = millisecondsInDay * 7;
          const millisecondsInMonth = millisecondsInDay * 30.44; // Approximate average
          const millisecondsInYear = millisecondsInDay * 365.25; // Approximate average

          const seconds = timeDifference / millisecondsInSecond;
          const minutes = timeDifference / millisecondsInMinute;
          const hours = timeDifference / millisecondsInHour;
          const days = timeDifference / millisecondsInDay;
          const weeks = timeDifference / millisecondsInWeek;
          const months = timeDifference / millisecondsInMonth;
          const years = timeDifference / millisecondsInYear;

          document.getElementById("seconds").textContent = seconds.toFixed(2);
          document.getElementById("minutes").textContent = minutes.toFixed(2);
          document.getElementById("hours").textContent = hours.toFixed(2);
          document.getElementById("days").textContent = days.toFixed(2);
          document.getElementById("weeks").textContent = weeks.toFixed(2);
          document.getElementById("months").textContent = months.toFixed(2);
          document.getElementById("years").textContent = years.toFixed(2);
        } else {
          document.getElementById("result").innerHTML =
            "Please enter valid dates.";
        }
      }
    </script>
  </body>
</html>
<br />
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Tool Selection</title>
  </head>
  <body>
    <div class="container">
      <h1>Tool Selection</h1>
      <label for="category">Select a Tool:</label>
      <select id="category" onchange="showSelectedTool()">
        <option value="">Select a Tool</option>
        <option value="mortgage">Mortgage Calculator</option>
        <option value="bmi">BMI Calculator</option>
        <option value="currency">Currency Converter</option>
        <option value="loan">Loan Calculator</option>
        <option value="calorie">Calorie Calculator</option>
      </select>

      <!-- Mortgage Calculator Section -->
      <div id="mortgageSection" class="tool-section" style="display: none">
        <h2>Mortgage Calculator</h2>
        <label for="mortgageLoanAmount">Enter Loan Amount:</label>
        <input type="number" id="mortgageLoanAmount" />
        <label for="mortgageInterestRate">Enter Interest Rate (%):</label>
        <input type="number" id="mortgageInterestRate" />
        <label for="mortgageLoanTerm">Enter Loan Term (years):</label>
        <input type="number" id="mortgageLoanTerm" />
        <button onclick="calculateMortgage()">Calculate Mortgage</button>
        <div id="mortgageResult"></div>
      </div>

      <!-- BMI Calculator Section -->
      <div id="bmiSection" class="tool-section" style="display: none">
        <h2>BMI Calculator</h2>
        <label for="bmiWeight">Enter Weight (kg):</label>
        <input type="number" id="bmiWeight" />
        <label for="bmiHeight">Enter Height (m):</label>
        <input type="number" id="bmiHeight" />
        <button onclick="calculateBMI()">Calculate BMI</button>
        <div id="bmiResult"></div>
      </div>

      <!-- Currency Converter Section -->
      <div id="currencySection" class="tool-section" style="display: none">
        <h2>Currency Converter</h2>
        <label for="currencyAmount">Enter Amount:</label>
        <input type="number" id="currencyAmount" />
        <label for="fromCurrency">From Currency:</label>
        <select id="fromCurrency">
          <option value="KWD">Kuwaiti Dinar (KWD)</option>
          <option value="BHD">Bahraini Dinar (BHD)</option>
          <option value="OMR">Omani Rial (OMR)</option>
          <option value="JOD">Jordanian Dinar (JOD)</option>
          <option value="GBP">British Pound Sterling (GBP)</option>
          <option value="CHF">Swiss Franc (CHF)</option>
          <option value="EUR">Euro (EUR)</option>
          <option value="KYD">Cayman Islands Dollar (KYD)</option>
          <option value="USD">United States Dollar (USD)</option>
          <option value="CAD">Canadian Dollar (CAD)</option>
          <option value="AUD">Australian Dollar (AUD)</option>
          <option value="NZD">New Zealand Dollar (NZD)</option>
          <option value="SEK">Swedish Krona (SEK)</option>
          <option value="NOK">Norwegian Krone (NOK)</option>
          <option value="DKK">Danish Krone (DKK)</option>
          <option value="SGD">Singapore Dollar (SGD)</option>
          <option value="BND">Brunei Dollar (BND)</option>
          <option value="HKD">Hong Kong Dollar (HKD)</option>
          <option value="AED">United Arab Emirates Dirham (AED)</option>
          <option value="SAR">Saudi Riyal (SAR)</option>
        </select>
        <label for="toCurrency">To Currency:</label>
        <select id="toCurrency">
          <option value="KWD">Kuwaiti Dinar (KWD)</option>
          <option value="BHD">Bahraini Dinar (BHD)</option>
          <option value="OMR">Omani Rial (OMR)</option>
          <option value="JOD">Jordanian Dinar (JOD)</option>
          <option value="GBP">British Pound Sterling (GBP)</option>
          <option value="CHF">Swiss Franc (CHF)</option>
          <option value="EUR">Euro (EUR)</option>
          <option value="KYD">Cayman Islands Dollar (KYD)</option>
          <option value="USD">United States Dollar (USD)</option>
          <option value="CAD">Canadian Dollar (CAD)</option>
          <option value="AUD">Australian Dollar (AUD)</option>
          <option value="NZD">New Zealand Dollar (NZD)</option>
          <option value="SEK">Swedish Krona (SEK)</option>
          <option value="NOK">Norwegian Krone (NOK)</option>
          <option value="DKK">Danish Krone (DKK)</option>
          <option value="SGD">Singapore Dollar (SGD)</option>
          <option value="BND">Brunei Dollar (BND)</option>
          <option value="HKD">Hong Kong Dollar (HKD)</option>
          <option value="AED">United Arab Emirates Dirham (AED)</option>
          <option value="SAR">Saudi Riyal (SAR)</option>
        </select>
        <button onclick="convertCurrency()">Convert Currency</button>
        <div id="currencyResult"></div>

        <script>
          function convertCurrency() {
            const amount = parseFloat(
              document.getElementById("currencyAmount").value
            );
            const fromCurrency = document.getElementById("fromCurrency").value;
            const toCurrency = document.getElementById("toCurrency").value;

            // Replace the following lines with your conversion rates or logic
            const conversionRates = {
              KWD: 0.304, // Replace with actual conversion rate
              BHD: 2.651, // Replace with actual conversion rate
              OMR: 2.597, // Replace with actual conversion rate
              JOD: 0.708, // Replace with actual conversion rate
              GBP: 0.793, // Replace with actual conversion rate
              CHF: 0.892, // Replace with actual conversion rate
              EUR: 0.92, // Replace with actual conversion rate
              KYD: 1.22, // Replace with actual conversion rate
              USD: 1.0, // Replace with actual conversion rate
              CAD: 1.27, // Replace with actual conversion rate
              AUD: 1.37, // Replace with actual conversion rate
              NZD: 1.46, // Replace with actual conversion rate
              SEK: 8.68, // Replace with actual conversion rate
              NOK: 8.62, // Replace with actual conversion rate
              DKK: 6.25, // Replace with actual conversion rate
              SGD: 1.34, // Replace with actual conversion rate
              BND: 1.35, // Replace with actual conversion rate
              HKD: 7.78, // Replace with actual conversion rate
              AED: 3.67, // Replace with actual conversion rate
              SAR: 3.75, // Replace with actual conversion rate
            };

            if (
              fromCurrency in conversionRates &&
              toCurrency in conversionRates
            ) {
              const convertedAmount =
                (amount * conversionRates[toCurrency]) /
                conversionRates[fromCurrency];
              document.getElementById(
                "currencyResult"
              ).textContent = `${amount} ${fromCurrency} = ${convertedAmount.toFixed(
                2
              )} ${toCurrency}`;
            } else {
              document.getElementById("currencyResult").textContent =
                "Invalid currency selection.";
            }
          }
        </script>
      </div>

      <!-- Loan Calculator Section -->
      <div id="loanSection" class="tool-section" style="display: none">
        <h2>Loan Calculator</h2>
        <label for="loanAmount">Enter Loan Amount:</label>
        <input type="number" id="loanAmount" />
        <label for="loanInterestRate">Enter Interest Rate (%):</label>
        <input type="number" id="loanInterestRate" />
        <label for="loanTerm">Enter Loan Term (years):</label>
        <input type="number" id="loanTerm" />
        <button onclick="calculateLoan()">Calculate Loan</button>
        <div id="loanResult"></div>
      </div>

      <!-- Calorie Calculator Section -->
      <div id="calorieSection" class="tool-section" style="display: none">
        <h2>Calorie Calculator</h2>
        <label for="calorieIntake">Enter Daily Calorie Intake:</label>
        <input type="number" id="calorieIntake" />
        <label for="exercise">Enter Exercise Calories Burned:</label>
        <input type="number" id="exercise" />
        <button onclick="calculateCalories()">Calculate Calories</button>
        <div id="calorieResult"></div>
      </div>
    </div>

    <script>
      function showSelectedTool() {
        const category = document.getElementById("category").value;

        // Hide all tool sections
        const toolSections = document.getElementsByClassName("tool-section");
        for (let i = 0; i < toolSections.length; i++) {
          toolSections[i].style.display = "none";
        }

        // Show the selected tool section
        if (category) {
          const toolSection = document.getElementById(category + "Section");
          if (toolSection) {
            toolSection.style.display = "block";
          }
        }
      }

      // Mortgage Calculator Function
      function calculateMortgage() {
        const loanAmount = parseFloat(
          document.getElementById("mortgageLoanAmount").value
        );
        const interestRate = parseFloat(
          document.getElementById("mortgageInterestRate").value
        );
        const loanTerm = parseFloat(
          document.getElementById("mortgageLoanTerm").value
        );

        if (!isNaN(loanAmount) && !isNaN(interestRate) && !isNaN(loanTerm)) {
          const monthlyInterestRate = interestRate / 100 / 12;
          const numberOfPayments = loanTerm * 12;
          const monthlyPayment =
            (loanAmount * monthlyInterestRate) /
            (1 - Math.pow(1 + monthlyInterestRate, -numberOfPayments));

          document.getElementById(
            "mortgageResult"
          ).textContent = `Monthly Payment: $${monthlyPayment.toFixed(2)}`;
        } else {
          document.getElementById("mortgageResult").textContent =
            "Please enter valid numbers.";
        }
      }

      // BMI Calculator Function
      function calculateBMI() {
        const weight = parseFloat(document.getElementById("bmiWeight").value);
        const height = parseFloat(document.getElementById("bmiHeight").value);

        if (!isNaN(weight) && !isNaN(height) && height > 0) {
          const bmi = weight / (height * height);
          document.getElementById(
            "bmiResult"
          ).textContent = `BMI: ${bmi.toFixed(2)}`;
        } else {
          document.getElementById("bmiResult").textContent =
            "Please enter valid values.";
        }
      }

      // Currency Converter Function
      function convertCurrency() {
        const amount = parseFloat(
          document.getElementById("currencyAmount").value
        );
        const fromCurrency = document.getElementById("fromCurrency").value;
        const toCurrency = document.getElementById("toCurrency").value;

        // Implement currency conversion logic here
        // Example: Calculate the converted amount and update #currencyResult
        // Replace the following line with your conversion logic:
        const convertedAmount = amount * 1.0; // Replace 1.0 with your conversion rate
        document.getElementById(
          "currencyResult"
        ).textContent = `${amount} ${fromCurrency} = ${convertedAmount.toFixed(
          2
        )} ${toCurrency}`;
      }

      // Loan Calculator Function
      function calculateLoan() {
        const loanAmount = parseFloat(
          document.getElementById("loanAmount").value
        );
        const interestRate = parseFloat(
          document.getElementById("loanInterestRate").value
        );
        const loanTerm = parseFloat(document.getElementById("loanTerm").value);

        // Implement loan calculation logic here
        // Example: Calculate the loan details and update #loanResult
        // Replace the following line with your loan calculation logic:
        const monthlyPayment = 0.0; // Replace 0.0 with your calculated monthly payment
        document.getElementById(
          "loanResult"
        ).textContent = `Monthly Payment: $${monthlyPayment.toFixed(2)}`;
      }

      // Calorie Calculator Function
      function calculateCalories() {
        const calorieIntake = parseFloat(
          document.getElementById("calorieIntake").value
        );
        const exercise = parseFloat(document.getElementById("exercise").value);

        // Implement calorie calculation logic here
        // Example: Calculate daily calorie balance and update #calorieResult
        // Replace the following line with your calorie calculation logic:
        const calorieBalance = 0.0; // Replace 0.0 with your calculated balance
        document.getElementById(
          "calorieResult"
        ).textContent = `Calorie Balance: ${calorieBalance.toFixed(2)}`;
      }
    </script>
  </body>
</html>
