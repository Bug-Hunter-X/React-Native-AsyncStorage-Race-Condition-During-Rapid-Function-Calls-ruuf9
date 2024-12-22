# React Native AsyncStorage Race Condition

This repository demonstrates a bug related to race conditions when using AsyncStorage in React Native within functions that are called rapidly, such as during scrolling. Multiple concurrent AsyncStorage operations can lead to data corruption, unexpected behavior, or app crashes.

## Bug Description

The core issue is the lack of proper synchronization when multiple `setItem` and `getItem` operations occur simultaneously. This can result in inconsistent data retrieval or overwrite of data before it's fully written, producing unpredictable outcomes.

## Reproduction

The `bug.js` file illustrates the problematic scenario. Run the app and scroll rapidly through a list to trigger the bug.  You'll likely observe unexpected data displayed or application instability.

## Solution

The `bugSolution.js` file provides a solution utilizing Promises and `async/await` to correctly sequence AsyncStorage operations. This ensures that each operation completes before the next one begins, preventing race conditions.