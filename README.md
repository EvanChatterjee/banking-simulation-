 (`Interest Applied: ₹${interest.toFixed(2)}\nNew Balance: ₹${balance.toFixed(2)}`);
     = `Balance: ₹${balance.toFixed(2)}`;

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
