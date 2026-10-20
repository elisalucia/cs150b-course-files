

# 16.7 LAB: Bitcoin Price Analysis

In this lab, you'll analyze about five years of daily Bitcoin prices (BTC/USD) using the list skills from this chapter: indexing, iterating with `for` loops, slicing, and tracking a value while looping.

The file `BTCUSD_day.csv` has one row per day. The first row is a header, and the rows after it are ordered **newest to oldest**. Each row has 8 columns:

| Index | Column | Example use |
| --- | --- | --- |
| 0 | Unix Timestamp | not needed |
| 1 | Date (`YYYY-MM-DD`) | identifying the day |
| 2 | Symbol | not needed |
| 3 | Open | price at the start of the day |
| 4 | High | not needed |
| 5 | Low | not needed |
| 6 | Close | price at the end of the day |
| 7 | Volume | not needed |

**Important:** Every value read from a CSV file is a string. Use `float()` before comparing or doing math with prices. Dates stay as strings.

**Important:** Your functions will also be tested with a different data file, so do not hard-code any dates or prices.

## Step 1: `read_csv(csv_file)`

Open the file named by `csv_file` and use `csv.reader()` to read it. Append each row (a list of strings) to a list, and return that list of lists. Keep the header row.

For `BTCUSD_day.csv`, the returned list should have 1979 rows (the header plus 1978 days), and each row should have 8 elements.

*Hint:* The header is `data[0]`. When processing prices in later steps, loop over `data[1:]` to skip it.

## Step 2: `all_time_high(data)`

Return the date and closing price of the day with the **highest closing price** (column 6, not the High column). Return both values as a tuple: `date, price`.

*Hint:* Use a variable to keep track of the highest price seen so far, and update it (and the date) whenever you find a higher one.

## Step 3: `all_time_low(data)`

Return the date and closing price of the day with the **lowest closing price** (column 6, not the Low column), as a tuple: `date, price`.

*Hint:* Starting your tracking variable at `0` won't work for a minimum. Instead, start with the first data row's closing price and date.

## Step 4: `percent_change(data, start, end)`

`start` and `end` are date strings. Find the **opening** price on the `start` date and the **closing** price on the `end` date, then return the percent change:

```
((end_price - start_price) / start_price) * 100
```

Examples:

- `percent_change(data, '2015-11-09', '2017-03-08')` returns about `213.33`
- `percent_change(data, '2017-12-17', '2018-12-17')` returns about `-81.58`

## Step 5: `largest_intraday_percentage_change(data)`

The intraday change is the percent change from a day's opening price to that same day's closing price. Find the day with the largest intraday change, measured by **absolute value** (a 12% drop is bigger than a 9% gain). Return the date and the absolute percent change as a tuple: `date, change`.

*Hint:* You already wrote a function that calculates percent change. Can you call it with the same date for `start` and `end`?

## Step 6: `run_tests()`

Use this function to test your own code before submitting. For example, call each function and print the results, or use `if` statements to check that a result matches what you expect. Try testing with a small list of rows you create yourself, where you know the correct answer.

## Expected output

When all functions are complete, running the program should print:

```
Analysis of BTC/USD Price Data
BTC/USD reached its all time high on 2021-02-20 at a price of $56541.20
BTC/USD reached its all time low on 2015-10-09 at a price of $245.51
Percent change from 2015-10-09 to 2021-03-08: 21285.86%
Largest intraday change occurred on 2020-03-12 and was 30.76%
```

Plus anything your `run_tests()` function prints.
