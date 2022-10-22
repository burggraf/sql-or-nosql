# SQL or NoSQL?  Why not use both (with PostgreSQL)?

It's a tough decision for any developer starting a new project.  Should you store your data in a standard, time-tested SQL database, or go with one of the newer NoSQL document-based databases?  This seemingly simple decision can literally make or break your project down the line.  Choose correctly and structure your data well, and you may sail smoothly into production and watch your app take off.  Make the wrong choice and you could be headed for nightmares (and maybe even some major re-writes) before your app ever makes it out the door.

### Simplicity vs Power
There are tradeoffs with both SQL and NoSQL solutions.  Typically it's easier to get started with NoSQL data structures, especially when the data is complex or hierarchical.  You can just take a JSON data object from your front end code and throw it in the database, and be done with it.  But later when you need to access that data to answer some basic business questions, it's much more difficult.  A SQL solution makes it easier to gather data and draw conclusions down the line.  Let's look at an example:

Each day I track the food I eat, along with the number of calories in each item:

| Day    | Food Item | Calories | Meal |
|--------|-----------|----------|------|
| 01 Jan | Apple     | 72 | Breakfast |
| 01 Jan | Oatmeal   | 146 | Breakfast |
| 01 Jan | Sandwich  | 445 | Lunch |
| 01 Jan | Chips     | 280 | Lunch |
| 01 Jan | Cookie    | 108 | Lunch |
| 01 Jan | Mixed Nuts | 175 | Snack |
| 01 Jan | Pasta/Sauce | 380 | Dinner |
| 01 Jan | Garlic Bread | 200 | Dinner |
| 01 Jan | Broccoli | 32 | Dinner |

I also track the number of cups of water I drink and when I drink them:

| Day    | Time  | Cups |
|--------|-------|------|
| Jan 01 | 08:15 | 1    |
| Jan 01 | 09:31 | 1    |
| Jan 01 | 10:42 | 2    |
| Jan 01 | 12:07 | 2    |
| Jan 01 | 14:58 | 1    |
| Jan 01 | 17:15 | 1    |
| Jan 01 | 18:40 | 1    |
| Jan 01 | 19:05 | 1    |

And finally I track my exercise:

| Day    | Time  | Duration | Exercise |
|--------|-------|----------|----------|
| Jan 01 | 11:02 | 0.5 | Walking |
| Jan 02 | 09:44 | 0.75 | Bicycling |
| Jan 02 | 17:00 | 0.25 | Walking |

For each day I also track my current weight along with any notes for the day:

| Day    | Weight | Notes |
|--------|--------|-------|
| Jan 01 | 172.6  | This new diet is awesome! |
| Jan 14 | 170.2  | Not sure all this is worth it. |
| Jan 22 | 169.8  | Jogged past a McDonald's today. It was hard. |
| Feb 01 | 168.0  | I feel better, but sure miss all that greasy food. |

### Entering All That Data
That's a lot of different data that needs to be gathered, stored, retrieved, and later analyzed.  It's organzied pretty simply and easily, but the number of records varies from day to day.  On any given day I may have zero or more entries for food, water, and exercise, and I may have zero or one entry for weight & notes.
