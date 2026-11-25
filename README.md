# Budget Tracker & Analyser

An Arduino-based budgeting device that helps youths build healthy spending habits. Set a monthly balance and spending target, log your expense each day, and get an end-of-month analysis with light and sound feedback.

## Features

- **Set your balance and monthly target** using the knob and buttons, shown on the 4-digit display.
- **Log daily expenses** for up to 30 days.
- **Input validation:** a daily expense or target above the available balance triggers a red LED and a low buzzer tone.
- **End-of-month analysis** printed to the Serial Monitor:
  - Days lasted
  - Highest and lowest daily spending
  - Amount saved or overspent against your target
  - Average daily expense
  - Projected yearly savings or overspending if the trend continues
- **Feedback with lights and sound:**
  - Green LED and a happy melody: target met
  - Yellow LED and a happy melody: target met, but within 5% of the limit
  - Red LED and a sad melody: target exceeded
- **Graph data export:** outputs comma-separated data (balance, target, accumulated expense, daily expense) for each day, ready to plot.

## Hardware

- Arduino board with the Rich Shield (4-digit TM1637 display, potentiometer knob, buttons, LEDs, passive buzzer)

| Component | Pin |
|---|---|
| Red LED | D4 |
| Green LED | D5 |
| Blue LED | D6 |
| Yellow LED | D7 |
| Button K1 (confirm) | D8 |
| Button K2 (change digit) | D9 |
| TM1637 display CLK / DIO | D10 / D11 |
| Passive buzzer | D3 |
| Knob (potentiometer) | A0 |

## Libraries

- `RichShieldTM1637`
- `RichShieldPassiveBuzzer`

## How to use

1. Open `Budget_Tracker___Analyser.ino` in the Arduino IDE.
2. Install the Rich Shield libraries, then upload the sketch to your board.
3. Open the Serial Monitor at **9600 baud**.
4. Follow the prompts:
   - **Turn the knob** to set the selected digit (0-9).
   - **Press K2** to move to the next digit (the selected digit blinks).
   - **Press K1** to confirm.
5. Enter your **balance** (up to 9999), then your **monthly target** (cannot exceed the balance).
6. Enter your **expense for each day**. Tracking ends after 30 days, or earlier if a day's spending exceeds your remaining balance.
7. Read the analysis in the Serial Monitor and listen for the result melody.
8. Press **K1** to print the graph data, then the device resets for a new month.

## Graph output format

Each line printed between `=== GRAPH START ===` and `=== GRAPH ENDS ===` is:

```
balance,target,accumulated_expense,daily_expense
```

You can paste this into a spreadsheet or plotting tool to visualise your spending.

## Project info

Built with Arduino C++ as a school project on healthy financial habits for youths.
