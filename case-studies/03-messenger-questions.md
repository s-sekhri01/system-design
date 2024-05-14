# Facebook messenger case study

## Requirements

```
- User should be able to send messages to other users
- The messages should be delivered in real-time
- The user should be able to see a message history with other users
- The user should be able to see a list of the most recent conversations
```

## Back of the envelope calculations

**Task** - Come up with a basic data schema for the messenger app

### Entities and attributes

List all the entities that you think are necessary for the messenger app

```
- Entity 1
    - Attribute 1
    - Attribute 2
- Entity 2
    - Attribute 1
    - Attribute 2
```

### Estimations


**Question**: `What according to you would be the number of daily active users for the messenger app?`

**Answer**: `500M`

**Question**: `How many conversations do you think a user would have in a day?`

**Answer**: `5`

**Question**: `How many messages do you think would be exchanged in a conversation?`

**Answer**: `10`

**Question**: `What are the total number of messages exchanged in a day?`

**Answer**: `25 B`

**Question**: `What is the size of a message?`

**Answer**: `200 Bytes`

**Question**: `What is the total amount of data exchanged in a day?`

**Answer**: `5 TB`

## Major operations

**Think of the different screens in the messenger app and the backend APIs that would be required to support them**

Screen - **Home screen**
API calls - 
```
- Get all conversations(user_id)
- get_conversation(con_id)
```

Screen - **Chat screen**
```
- get_messages(conv_id, user_id)
- post_messages(conv_id, sender_id, receiver_id, text)
```
---
## Design decisions

**Question**: `Will your system be read-heavy or write-heavy?`

**Answer**: `Both`

**Question**: `Out of the 3 parts of the CAP theorem, which one would you choose for your system?`

**Answer**: `Consistency`

---
## Sharding

**Question**: `Do you need to shard your database?`

**Answer**: `Yes`

**Question**: `What would be the different candidate keys for sharding?`

**Answer**:
```
- User Id
- Conversation ID
```

### Candidate key 1

**Question**: `List down the number of reads and writes required for each operation`

**Answer**:
```
- get conversations
    - 1
- get messages
    - 1
- send messages
    - 2
```

### Candidate key 2

**Question**: `List down the number of reads and writes required for each operation`

**Answer**:
```
- get conversations
    - N
- get messages
    - 1
- send message
    - 1
```

**Final choice**: ` `

**Question**: `Do you require any other component to optimise your sharding strategy?`

**Answer**: 
```
Cache, to reduce read requests
```

---
## Design compliance

## Consistency
**Question** - `If you chose high consistency, how would you ensure that the system is consistent?`

**Answer** - 
```
By writing in shard B first and then writing in shard A
```

## Database

**Question** - `What kind of database would you choose for the messenger app?`

**Answer** - 
```
No SQL, HBase or casssandra due to high write throughput
```









