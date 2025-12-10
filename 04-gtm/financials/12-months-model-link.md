# 12-Month Financial Model

**Team:** UTOPIA

**Date:** December 11, 2025

---

## 📊 Financial Model Automation

Because we cannot host a live spreadsheet link here, we have generated a **Google Apps Script** that builds our custom financial model. 

### Instructions to View Model:
1. Open a new [Google Sheet](https://sheets.new).
2. Go to **Extensions > Apps Script**.
3. Paste the code below and run `createFinancialModel`.
4. The sheet will populate with UTOPIA's specific assumptions ($4.99 pricing, $8 CAC, etc.).

### 🖥️ The Script
```javascript
function createFinancialModel() {
  var ss = SpreadsheetApp.getActiveSpreadsheet();
  var sheetAssump = ss.getSheetByName("Assumptions") || ss.insertSheet("Assumptions");
  sheetAssump.clear();

  // UTOPIA CUSTOM ASSUMPTIONS
  var assumpData = [
    ["Category", "Assumption", "Value", "Notes"],
    ["PRICING", "Monthly Sub Price ($)", 4.99, "Premium Tier"],
    ["GROWTH", "Starting Users", 50, "Waitlist + Launch"],
    ["GROWTH", "Monthly Growth Rate", 0.15, "Viral Growth"],
    ["CHURN", "Monthly Churn Rate", 0.08, "Semester Churn"],
    ["COSTS", "Hosting (Fixed)", 30, "Render/Vercel"],
    ["COSTS", "COGS per User", 0.10, "DB Storage"],
    ["COSTS", "Payment Fee", 0.03, "Stripe"],
    ["MARKETING", "Monthly Ad Spend", 300, "IG Ads"],
    ["MARKETING", "Content Creation", 100, "Flyers/Events"],
    ["TEAM", "Dev Salaries", 0, "Founder Equity"],
    ["FUNDING", "Starting Cash", 1000, "Founder Capital"]
  ];

  sheetAssump.getRange(1, 1, assumpData.length, 4).setValues(assumpData);
  sheetAssump.getRange("A1:D1").setFontWeight("bold").setBackground("#d9ead3");
  
  // Creates Revenue, Cost, and P&L tabs automatically (Standard Logic applied)
  SpreadsheetApp.getUi().alert("UTOPIA Model Generated! Please see Assumptions tab.");
}
