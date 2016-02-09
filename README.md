# You Need a Budget / JPMorgan Chase Reconciler

A tool to assist with reconcilation of data between the [You Need a Budget](http://www.youneedabudget.com) software and one or more accounts at [JPMorgan Chase](https://www.chase.com).

**DISCLAIMER: Use at your own risk. I am not liable for anything this software does or anything you do as a result of using it.**

## Requirements

Only a [PHP](http://php.net) installation is required. I've only tested on 5.6, but it should work on any supported version.

## Usage

Invoke the `reconcile` script where the first argument is the path to a [YNAB CSV export](http://classic.youneedabudget.com/support/article/opening-a-csv-export-in-excel) and all subsequent arguments are paths to [JPMorgan Chase CSV exports](http://help.bookkeeping.godaddy.com/entries/22242916-Download-a-CSV-from-Chase-Bank).

```
reconcile ynab.csv jpmc1.csv ... jpmcN.csv
```

## How It Works

The reconciler locates transactions that meet either of the following criteria:

1. A transaction with the same amount does not exist in either of YNAB or JPMC; or
2. The quantities of transactions with the same amount differ between YNAB and JPMC.

These criteria generally indicate at least one of the following conditions to be met by one or more transactions from the reconciler output:

1. They were entered into one of YNAB or JPMC and not the other;
2. They have been removed from JPMC since they were entered into YNAB; or
3. They have had their amounts changed in JPMC since being entered into YNAB.

The output is intended to help you by finding transactions that may be missing from or have inconsistent amounts between YNAB or JPMC.

## Why I Wrote It

YNAB has a [reconcilation](http://classic.youneedabudget.com/support/article/how-to-reconcile) feature, but it leaves a lot of the grunt work of reconciling accounts to be done manually by the user, which I don't consider to be very useful.

While I believe it's good to give the user the choice of what changes to enter, I think a computer can be helpful in finding what changes may need to be entered.

## License

This software is licensed under the [MIT License](https://opensource.org/licenses/MIT).
