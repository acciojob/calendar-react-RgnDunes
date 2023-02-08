# boilerplate-react-functional-public

## Explanation

The code is a React component that creates a calendar. Here is an explanation of each section of the code:

1. Importing required libraries:

```
import React, { useState } from "react";
```

Here, React is imported from the 'react' library, and the useState hook from the 'react' library is also imported.

2. Defining constant variables:

```
const months = [
  "January",
  "February",
  "March",
  "April",
  "May",
  "June",
  "July",
  "August",
  "September",
  "October",
  "November",
  "December",
];
const days = ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"];
```

The months constant variable is an array of 12 month names, and the days constant variable is an array of 7 days of the week.

3. Setting up component state with useState hook:

```
const [selectedMonth, setSelectedMonth] = useState(new Date().getMonth());
const [selectedYear, setSelectedYear] = useState(new Date().getFullYear());
const [showYearInput, setShowYearInput] = useState(false);
```

Three state variables are defined using the useState hook:
selectedMonth: The currently selected month. This is initialized to the current month using new Date().getMonth().
selectedYear: The currently selected year. This is initialized to the current year using new Date().getFullYear().
showYearInput: A boolean value that determines whether to show the year input box or not. This is initialized to false.

4. Defining functions to handle changes in state:

```
const handleMonthChange = (event) => {
  setSelectedMonth(event.target.selectedIndex);
};

const handleYearDoubleClick = () => {
  setShowYearInput(true);
};

const handleYearInput = (event) => {
  setSelectedYear(event.target.value);

  document.addEventListener("keyup", function (event) {
    if (event.keyCode === 13) {
      setShowYearInput(false);
    }
  });
};

const handlePreviousMonth = () => {
  if (selectedMonth === 0) {
    setSelectedMonth(11);
    setSelectedYear(selectedYear - 1);
  } else {
    setSelectedMonth(selectedMonth - 1);
  }
};

const handleNextMonth = () => {
  if (selectedMonth === 11) {
    setSelectedMonth(0);
    setSelectedYear(selectedYear + 1);
  } else {
    setSelectedMonth(selectedMonth + 1);
  }
};

const handlePreviousYear = () => {
  setSelectedYear(selectedYear - 1);
};

const handleNextYear = () => {
  setSelectedYear(selectedYear + 1);
};
```

These functions are defined to handle changes in the component's state variables.

The component has several event handlers to manage changes to these state variables, such as handleMonthChange, handleYearDoubleClick, handleYearInput, handlePreviousMonth, handleNextMonth, handlePreviousYear, and handleNextYear.

5. The daysInMonth function takes a month and year as inputs and returns the number of days in that month of that year.

6. The code defines a function createTableCells that creates table cells for a calendar. It takes two arguments, selectedMonth and selectedYear, which are used to determine the number of days in the selected month and year, and the starting day of the selected month. The function creates an array of cells, which will be used to create table rows.
   The number of days in the selected month is calculated using the daysInMonth function. The starting day of the selected month is calculated using the Date object and the getDay method.
   The function then uses two nested for loops to create table cells. The outer loop runs 6 times, representing the 6 rows of the calendar. The inner loop runs 7 times, representing the 7 columns of the calendar. The cellId is set as a string in the format "cell{i + j + 1}".
   For the first row, if j is less than startingDay, an empty cell is added to the row. If date is greater than numberOfDays, an empty cell is added to the row. Otherwise, the date is added to the cell. If the selected date, month, and year match the current date, month, and year, the cellId is set to "today". The row is then added to the cells array.
   Finally, the createTableCells function returns the cells array.

IN OTHER WORDS

    6.1 The function takes in two arguments, selectedMonth and selectedYear, which are the month and year selected by the user.

    6.2 numberOfDays is calculated by calling daysInMonth function which returns the number of days in the selected month and year.

    6.3 startingDay is calculated by creating a new Date object with the selected year and month and calling the getDay method on it, which returns the day of the week of the first day of the selected month.

    6.4 The for loop is used to iterate over 6 rows of the calendar table.

    6.5 For each row, there is another for loop that iterates over 7 columns of the table, representing the 7 days of the week.

    6.6 In each iteration of the inner loop, a new table cell is created with an id attribute and pushed into the row array. The id of each cell is constructed by concatenating a string "cell" with the index of the cell.

    6.7 If it's the first row and the column index is less than the startingDay, a blank cell is added to the row array.

    6.8 If the date has exceeded the numberOfDays, another blank cell is added to the row array.

    6.9 If the selected year and month match the current year and month, and the date matches the current date, the cell is given an id of "today".

    6.10 The row is then added to the cells array.

    6.11 The createTableCells function finally returns the cells array, which represents the 2D array of table cells for the calendar.
