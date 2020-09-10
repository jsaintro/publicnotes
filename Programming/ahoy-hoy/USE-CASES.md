Title: Create On-Call Schedule
Primary Actor: Manager

1. Manager authenticates to application
1. Manager creates a new On-Call schedule
1. Manger chooses how often to rotate On-Call based on schedule

Title: Add Engineer to On-Call Schedule
Primary Actor: Manager

1. Manager authenticates to application
10. Manager picks an On-Call schedule 
11. Manger adds engineer to On-Call schedule

Title: Delete On-Call member
Primary Actor: Manager

1. Manager authenticates to application
10. Manager picks an On-Call schedule
13. System displays a list Engineers for this on-Call schedule
14. Manager chooses the engineer to be removed

Title: Notify On-Call
Primary Actor: Manager
Success Scenario:

1. Manager authenticates to application
2. Manager picks an on-call schedule
3. Selects On-Call to Notify
4. System looks at On-Call schedule and selects engineer
5. System sends notification email to engineer

Title: Display Schedule
Primary Actor: Engineer
Success Scenario:

1. Engineer authenticates to application
2. Engineer select an on-call schedule
3. System displays selected schedule

Title: Trade Places
Primary Actor: Engineer
Success Scenario:

1. Engineer authenticates to application
2. Engineer selects On-Call schedule
3. System displays selected schedule
4. Engineer selects person to trade with
5. System notifies both Engineers that the swap was made via email
  
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzNDk5OTM4NjIsMTE5MzA3Mjc0XX0=
-->