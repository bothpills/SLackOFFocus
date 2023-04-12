# SLackOFFocus
Local Slack productivity plugin base code.

An application to help improve focus of a working team. 

Predefine a specific amount of time for the duration of work sessions (e.g. 20 minutes), in which team members will be able to send messages to colleagues but will not be able to receive them. At the end of each micro work session a communication window will open for a predefined amount of time (e.g. 5 minutes), in which team members will receive the messages they were waiting for and will be able to communicate normally with the team. At the end of the communication window a new work session is started and the focus is resumed.

---

Next features:

  - Enable to not start a new work session for member that still talking. The following work session will last less time, discounting the extra time used in orther to maintain the team synchronized.
  - Enable users to send messages during the work session. Messages should go into standby mode, and not be rejected.
  

---

This is an initial experiment. I plan to create a systemwise solution so that all communication that does not come from the administrator is temporarily blocked.
