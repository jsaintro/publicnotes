Title: Create On-Call Schedule
Primary Actor: Manager

1. Manager authenticates to application
1. Manager creates a new On-Call schedule
1. Manger selects how often to rotate On-Call based on schedule

Title: Add Engineer to On-Call Schedule
Primary Actor: Manager

1. Manager authenticates to application
10. Manager selects an On-Call schedule 
11. Manger adds engineer to On-Call schedule

Title: Delete On-Call member
Primary Actor: Manager

1. Manager authenticates to application
10. Manager selects  an On-Call schedule
13. System displays a list Engineers for this on-Call schedule
14. Manager select the engineer to be removed

Title: Notify On-Call
Primary Actor: Manager
Success Scenario:

1. Manager authenticates to application
16. Manager selects an on-call schedule
17. Selects On-Call to Notify
18. System looks at On-Call schedule and selects engineer
19. System sends notification email to engineer

Display Schedule:
Title: Trade Places
Primary Actor: Engineer
Success Scenario:

1. Engineer authenticates to application
21. Engineer selects On-Call schedule
  
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTY5NTY0MDQzXX0=
-->