# UI

https://www.nngroup.com/articles/toggle-switch-guidelines/

Summary: Toggle switches are digital on/off switches. They prompt users to choose between two mutually exclusive options and always have a default value. Toggles should provide immediate results, giving users the freedom to control their preferences as needed.

# React enzyme testing

https://github.com/airbnb/enzyme/issues/1002

"I'd generally recommend using only shallow as much as possible, and only making assertions on which components your thing renders - in other words, if A renders B which renders C, your A tests shouldn't know anything about C, and should only be asserting that A renders B with the right props. Your _B_ tests should be asserting things about C." **[ljharb](/ljharb) ** commented [on Jul 26, 2017](#issuecomment-318102035)
