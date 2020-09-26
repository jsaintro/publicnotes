# Use Cases
Nouns are bolded as potential objects and verbs are italicised as potential methods.

### Title: Create On-Call Schedule
Primary Actor: Manager
Success Scenario:
1. **Manager** *authenticates* to **application**
1. **Manager** *creates* a new **On-Call** **schedule**
1. **Manger** *chooses how often to rotate* **On-Call** based on **schedule**

### Title: Add Engineer to On-Call Schedule
Primary Actor: Manager
Success Scenario:
1. **Manager** *authenticates* to application
10. **Manager** *picks* an **On-Call** **schedule** 
11. **Manger** *adds* **engineer** to **On-Call** **schedule**

### Title: Delete On-Call member
Primary Actor: Manager
Success Scenario:
1. **Manager** authenticates to **application**
10. **Manager** *picks* an **On-Call** **schedule**
13. **System** *displays* a **list** **Engineers** for this **On-Call** **schedule**
14. **Manager** *chooses* the **engineer** to be removed

### Title: Notify On-Call
Primary Actor: Manager
Success Scenario:
1. **Manager** *authenticates* to **application**
2. **Manager** *picks* an **on-call** schedule
3. Selects **On-Call** to Notify
4. **System** looks at **On-Call** **schedule** and selects **engineer**
5. **System** sends notification **email** to **engineer**

### Title: Display Schedule
Primary Actor: Engineer
Success Scenario:
1. **Engineer** authenticates to **application**
2. **Engineer** picks an **on-call** **schedule**
3. **System** displays selected **schedule**

### Title: Trade Places
Primary Actor: Engineer
Success Scenario:
1. **Engineer** authenticates to **application**
2. **Engineer** picks an **On-Call** **schedule**
3. **System** displays selected **schedule**
4. **Engineer** chooses an **Engineer** to trade **places** with
5. **System** notifies both **Engineers** that the swap was made via **email**
  
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcwMDgyMjYxNSwxOTg0NTcyOTA1LC0xNT
Y4ODI2MTY2LDExOTMwNzI3NF19
-->