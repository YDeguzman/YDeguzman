<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>Loan Eligibility</title>
 <script type="module" src="https://cdn.jsdelivr.net/npm/@ionic/core/dist/ionic/ionic.esm.js"></script>
 <script nomodule src="https://cdn.jsdelivr.net/npm/@ionic/core/dist/ionic/ionic.js"></script>
 <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@ionic/core/css/ionic.bundle.css" />
</head>
<body>
 <ion-header>
   <ion-toolbar>
     <ion-title>Loan Eligibility</ion-title>
   </ion-toolbar>
 </ion-header>
 
 <ion-content class="ion-padding">
   <ion-item>
     <ion-label position="floating">Monthly Income</ion-label>
     <ion-input id="income" type="number" placeholder="Enter your income"></ion-input>
   </ion-item>
   
   <ion-item>
     <ion-label position="floating">Loan Type</ion-label>
     <ion-select id="loanType" placeholder="Select Loan Type">
       <ion-select-option value="personal">Personal</ion-select-option>
       <ion-select-option value="home">Home</ion-select-option>
       <ion-select-option value="auto">Auto</ion-select-option>
     </ion-select>
   </ion-item>
   
   <ion-item>
     <ion-label>Existing Debts</ion-label>
     <ion-checkbox id="hasDebts"></ion-checkbox>
   </ion-item>
   
   <ion-button expand="block" onclick="checkEligibility()">CHECK ELIGIBILITY</ion-button>
   
   <ion-card>
     <ion-card-header>
       <ion-card-title>Eligibility Result</ion-card-title>
     </ion-card-header>
     <ion-card-content id="result">Your eligibility result will appear here...</ion-card-content>
   </ion-card>
 </ion-content>

 <script>
   function checkEligibility() {
     const income = parseFloat(document.getElementById('income').value);
     const loanType = document.getElementById('loanType').value;
     const hasDebts = document.getElementById('hasDebts').checked;
     
     const multipliers = { personal: 10, home: 20, auto: 15 };
     let eligibility = income * (multipliers[loanType] || 0);
     
     if (hasDebts) eligibility *= 0.7;
     
     document.getElementById('result').innerHTML = `Your eligibility is: ${eligibility}`;
   }
 </script>
</body>
</html>
