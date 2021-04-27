TASK

Given a set of lottery TICKETS, write a script that determines whether the list contains a winning ticket specified by WINNING_NUMBERS.

You may assume: 

 * The numbers in each ticket and the winning numbers are not provided in any specific order. A winning ticket must have the same numbers as the winning numbers, but does not need to be in the same order. 
 * Each lottery ticket and the set of winning numbers has six numbers. 
 * You can create any functions you like, but please limit yourself to the standard NodeJS library (ES6+ is ok).

const WINNING_NUMBERS = [25, 20, 27, 28, 58, 59];

const TICKETS = [
    [7, 58, 28, 59, 20, 27],
    [1, 2, 3, 4, 5, 6],
    [25, 58, 28, 27, 59, 20],
    [25, 19, 27, 28, 58, 59],
    [25, 58, 28, 59, 20, 27]
];


