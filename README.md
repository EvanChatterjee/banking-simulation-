// Banking Simulator - Interest Calculation

let balance = 0; // User's balance

// Function to set initial balance
function setInitialBalance() {
    let amount = parseFloat(document.getElementById("initialAmount").value);
    if (!isNaN(amount) && amount >= 0) {
        balance = amount;
        updateBalanceDisplay();
    } else {
        alert("Please enter a valid amount.");
    }
}

// Function to deposit money
function deposit() {
    let amount = parseFloat(document.getElementById("depositAmount").value);
    if (!isNaN(amount) && amount > 0) {
        balance += amount;
        updateBalanceDisplay();
    } else {
        alert("Please enter a valid deposit amount.");
    }
}

// Function to withdraw money
function withdraw() {
    let amount = parseFloat(document.getElementById("withdrawAmount").value);
    if (!isNaN(amount) && amount > 0) {
        if (amount > balance) {
            alert("Insufficient balance!");
        } else {
            balance -= amount;
            updateBalanceDisplay();
        }
    } else {
        alert("Please enter a valid withdrawal amount.");
    }
}

// Function to calculate Simple Interest
function calculateSimpleInterest(principal, rate, time) {
    return (principal * rate * time) / 100;
}

// Function to calculate Compound Interest
function calculateCompoundInterest(principal, rate, time) {
    return principal * Math.pow((1 + rate / 100), time) - principal;
}

// Function to apply interest to balance
function applyInterest(type) {
    let rate = parseFloat(document.getElementById("interestRate").value);
    let time = parseFloat(document.getElementById("timePeriod").value);
    if (!isNaN(rate) && !isNaN(time) && rate > 0 && time > 0) {
        let interest = 0;
        if (type === "simple") {
            interest = calculateSimpleInterest(balance, rate, time);
        } else if (type === "compound") {
            interest = calculateCompoundInterest(balance, rate, time);
        }
        balance += interest;
        updateBalanceDisplay();
        alert(`Interest Applied: ₹${interest.toFixed(2)}\nNew Balance: ₹${balance.toFixed(2)}`);
    } else {
        alert("Please enter valid interest rate and time period.");
    }
}

// Function to update balance display
function updateBalanceDisplay() {
    document.getElementById("balanceDisplay").innerText = `Balance: ₹${balance.toFixed(2)}`;
}

// Adding buttons and input fields dynamically
document.write(`
    <div>
        <h2>Banking Simulator</h2>
        <p id="balanceDisplay">Balance: ₹0.00</p>
        <input type="number" id="initialAmount" placeholder="Set Initial Balance">
        <button onclick="setInitialBalance()">Set Balance</button>
        <br><br>
        <input type="number" id="depositAmount" placeholder="Deposit Amount">
        <button onclick="deposit()">Deposit</button>
        <br><br>
        <input type="number" id="withdrawAmount" placeholder="Withdraw Amount">
        <button onclick="withdraw()">Withdraw</button>
        <br><br>
        <input type="number" id="interestRate" placeholder="Interest Rate (%)">
        <input type="number" id="timePeriod" placeholder="Time Period (Years)">
        <button onclick="applyInterest('simple')">Apply Simple Interest</button>
        <button onclick="applyInterest('compound')">Apply Compound Interest</button>
    </div>
`);
