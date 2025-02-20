# Firebase Firestore Transaction Error: Missing Document Creation

This repository demonstrates an uncommon error in Firebase Firestore transactions where attempting to set a document within a transaction fails if the document doesn't already exist. The code assumes that `transaction.set()` will create the document if it's missing, leading to race conditions and potential data inconsistencies. This issue highlights the importance of handling document creation within Firestore transactions atomically to ensure data integrity.

## Problem
The provided `bug.js` file contains a code snippet that attempts to increment a counter in Firestore using a transaction. However, it does not correctly handle the case where the document doesn't exist. This results in the transaction failing if multiple clients attempt to create the document concurrently.

## Solution
The `bugSolution.js` file demonstrates the correct way to handle document creation within a transaction.  By using `transaction.get()` first and `transaction.set()` conditionally only if the document doesn't exist, the operation remains atomic.

## How to Reproduce
1. Clone this repository.
2. Configure your Firebase project and install the required dependencies.
3. Run `bug.js` and observe the potential error.
4. Compare the results with those of `bugSolution.js`.