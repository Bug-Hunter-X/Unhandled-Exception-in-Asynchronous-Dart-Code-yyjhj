# Unhandled Exception in Asynchronous Dart Code

This repository demonstrates a common error in asynchronous Dart code: failing to properly handle exceptions in asynchronous operations, specifically the omission of `rethrow` in `catch` blocks within `async` functions.  Improper exception handling can lead to unexpected behavior or silent failures.

## Bug Description

The `bug.dart` file contains an `async` function (`fetchData`) that fetches data from a remote API.  If the API request fails (e.g., network error or non-200 status code), an exception is caught. However, because `rethrow` is missing, the exception is swallowed locally. This prevents higher-level error handling routines from responding to the failure.

## Solution

The `bugSolution.dart` file presents a corrected version. By adding `rethrow`, the exception is properly propagated up the call stack allowing higher-level handling mechanisms, such as `try-catch` blocks in calling functions, to address the failure gracefully.

## How to Run

1.  Clone this repository.
2.  Ensure you have Dart SDK installed.
3.  Run the buggy code: `dart bug.dart` (observe the lack of output upon failure).
4.  Run the corrected code: `dart bugSolution.dart` (observe the proper exception handling).
