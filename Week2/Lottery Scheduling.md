# Lottery Scheduling: Flexible Proportional-Share Resource Management



* In this paper, the authors proposed a lottery scheduling using a proportional share algorithm.
* The motivation of this paper is that legacy schedulings are focused on priorities or fairness so that they are not suitable for applications such as databases that require interactive response.
* The maid idea is to determine the next process to run through generating random number.
  * Processes that need to be executed more often are given lots of lottery tickets, so they are more likely to run.
* The authors described lottery currency, lottery ticket transfer, lottery ticket expansion, etc. and argue that because of these features it can be applied to memory and IO systems as well as CPU.
* However, lottery scheduling has some severe drawbacks thus it is not implemented a real operating system.
  * It is difficult to decide on how much assigning a lottery to a process and 
  * scheduling is not well done when there is a lot of IO work.