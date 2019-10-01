# Fine Grained Energy Accounting on Smartphones with Eprof

## Motivation

* Unlike desktop applications, smartphone applications are difficult to analyze power consumption.
  * There is an asynchronous feature that power consumption continues after the application terminates.

## Findings

* 65-75% of the power of free applications is consumed by third-party applications.
* Authors have found the location of code that causes energy bugs through eprof.
* IO requests accounted for most of the application's power consumption, and IOs are clustered because of some routine work.

## Solution

* This paper first presents the fine-grained energy profiler which is *eprof* to analyze the energy consumption of smartphone applications.
* The last-trigger policy allows us to capture asynchronous power consumption of applications on modern smartphones.
* By suggesting a tool that shows new IO statistics called bundles, it helps application developers quickly understand and optimize power consumption.

## Future works

* Eprof can be adopted at the compiler level for static analysis to automate energy consumption.
* Eprof can help to develop OS scheduling algorithm.