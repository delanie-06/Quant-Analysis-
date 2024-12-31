# **Pairs Trading Strategy: Sensex vs. Nifty**

This repository implements a **market-neutral pairs trading strategy** based on the relative performance of the Sensex and Nifty indices. The strategy exploits deviations between the ratio of the two indices and its rolling average to generate buy/sell signals. Designed in Excel, it is a simple and adaptable framework for backtesting and analyzing quantitative trading strategies.

---

## **Overview**

Pairs trading is a statistical arbitrage strategy that involves trading two correlated financial instruments. This project compares the **Sensex-to-Nifty ratio** with its **10-day rolling average** to identify trading opportunities:

- **Signal = +1**: Buy Sensex, Sell Nifty (Ratio < Rolling Average)
- **Signal = -1**: Sell Sensex, Buy Nifty (Ratio > Rolling Average)
- **Signal = 0**: No trade (Ratio = Rolling Average)

The returns from the strategy are calculated based on the relative performance of the indices.

---

## **How It Works**

### **1. Input Data**
The strategy uses:
- **Sensex closing prices**
- **Nifty closing prices**

### **2. Key Calculations**
- **Ratio (Sensex/Nifty)**: The daily ratio of Sensex to Nifty.
- **Rolling Average**: A 10-day moving average of the ratio.
- **Signals**: Generated by comparing the current ratio to the rolling average:
  - `+1`: Buy Sensex, Sell Nifty
  - `-1`: Sell Sensex, Buy Nifty
  - `0`: No trade
- **Strategy Returns**:
  - If Signal = +1: `Strategy Return = Sensex Return - Nifty Return`
  - If Signal = -1: `Strategy Return = Nifty Return - Sensex Return`
  - If Signal = 0: `Strategy Return = 0`

### **3. Metrics**
- **Total Return**: The cumulative return of the strategy.
- **Average Return**: Mean return per trade.
- **Maximum Return**: Best-performing trade.
- **Minimum Return**: Worst-performing trade.
- **Sharpe Ratio (Optional)**: Risk-adjusted return.

---

## **Implementation in Excel**

### **Step-by-Step Guide**
1. **Input Data**:
   - Add Sensex and Nifty closing prices in separate columns.

2. **Calculate Ratio**:
   - Formula: `=Sensex/Nifty`

3. **Calculate Rolling Average**:
   - Use Excel's `AVERAGE` function: `=AVERAGE(previous 10 cells of the Ratio column)`

4. **Generate Signals**:
   - Formula: `=IF(Current Ratio > Rolling Average, -1, IF(Current Ratio < Rolling Average, 1, 0))`

5. **Calculate Returns**:
   - **Sensex Return**: `(Current Day Sensex Price / Previous Day Sensex Price) - 1`
   - **Nifty Return**: `(Current Day Nifty Price / Previous Day Nifty Price) - 1`
   - **Strategy Return**:
     - Formula: `=IF(Signal=1, (Sensex Return - Nifty Return), IF(Signal=-1, (Nifty Return - Sensex Return), 0))`

6. **Summary Metrics**:
   - Total Return: `=SUM(Strategy Returns Column)`
   - Average Return: `=AVERAGE(Strategy Returns Column)`
   - Min Return: `=MIN(Strategy Returns Column)`
   - Max Return: `=MAX(Strategy Returns Column)`

---

## **Project Files**
- **Excel Workbook**: Contains the implementation of the strategy with formulas and sample data.

---

## **Conclusion**
This pairs trading strategy provides a market-neutral framework to capitalize on relative mispricings between the Sensex and Nifty indices. By analyzing deviations from the rolling average, the strategy identifies profitable trading opportunities while minimizing overall market exposure.

---

## **Future Enhancements**
- Automating data retrieval using APIs (e.g., Yahoo Finance, NSE API).
- Incorporating transaction costs for realistic return calculations.
- Extending the strategy to other pairs of indices or stocks.

