# SNHU-CS-360-Final-Project
Repo for final project of CS360: Mobile Architect and Programming

## Response Questions

### Briefly summarize the requirements and goals of the app you developed. What user needs was this app designed to address?

The goal of this assignemnt was to create an inventory management app using Android Studio. It worked with a database of user accounts,
items, and inventories. Users needed to be able create and sign in to said accounts, view the items in their inventory, change item quantities, and delete and add
items. The app also sends a SMS notification when an item runs out of stock.

### What screens and features were necessary to support user needs and produce a user-centered UI for the app? How did your UI designs keep users in mind? Why were your designs successful?

There are 3 main screens, the login/signup on startup, inventory view, and new item form. Each featured various data transfers between the user and the app's database. such
as the login/signup screen taking a username and password as input when retrieving or creating a user's account. My mentality with designing user-friendly UI was
to minimize or remove any of the midly frustrating quirks I noticed during development and testing--picturing myself as a user. For example, the inventory
screen displays items on a grid, one row per item, that scrolls vertically. While testing, I saw that the FAB (floating action button) in the bottom-right
corner for adding new items blocked the bottom rows when you scrolled all the way to the bottom. I found that annoying, so I figured a lot of other users
would too, so I added enough bottom padding to the scrolling widget for rows to be scrolled above the FAB. I think this method of anticipating and addressing
potential user frustrations made my designs successful.

### How did you approach the process of coding your app? What techniques or strategies did you use? How could those techniques or strategies be applied in the future?

I coded modularly partly because I believed it was the most efficient strategy and partly because I was using Java and it worked well with OOP (object-oriented programming).
This meant incrementally developing each feature to completion with as few cross-dependencies as I could manage. I tried to follow the model MVC (model-view-controller)
design pattern which splits software into logic, UI design, and the interface between the two. These are well-documented strategies that I could apply
to most future projects because they're based in generally effective techniques.

#### How did you test to ensure your code was functional? Why is this process important, and what did it reveal?

Since I developed my code incrementally, I would test it frequently using Android Studio's emulator and app inspection tools. For example, I used
the inspection tool to verify that my app was changing the database as expected. Testing is important for making sure development is effective.
It would reveal unforeseen bugs like item's data being overwritten when scrolling through an inventory or their quantities becoming -1
due to integer overflow when attempting to convert from a string of a large number.

#### Consider the full app design and development process from initial planning to finalization. Where did you have to innovate to overcome a challenge?

One challenge I had as someone who doesn't have a lot of experience with SQL or databases was figuring out a way to store what I initially
thought could only be an array in a relational database--something that I understood wasn't recommended. Instead of an Inventories table having an
items column that's an array of Item ids, most sources I found on the subject suggested a different solution. I could instead use an InventoryItems
table which would have user_id, item_id, and quantity columns. Each row in this table represents a unique item in a user's inventory. To get
all the items in a user's inventory, then, only requires finding the rows with their user_id. This worked out pretty well I think.

#### In what specific component of your mobile app were you particularly successful in demonstrating your knowledge, skills, and experience?

One thing I'm particularly proud of is my use of the RecyclerView widget for the inventory display. It's essentially just a more complicated
way to display a scrollable list of widgets that's better for performance than the traditional ScrollView because instead of loading all
its widgets at once it "recycles" what are are called ViewHolders. That way, the app doesn't waste resources loading a bunch of off-screen
widgets. The added complexity of implementing RecyclerView comes from needing to explictly define these ViewHolders and how they're recycled
via code. Learning to do so and designing it to fit my specific application's needs was the most difficult part of this project for me. It
was also completely optional because, like I said, I could have just used a ScrollView; in fact, that's exactly what I did until, as I was
doing my final revisions before submitting the assignment, I realized there was at least one thing I could still improve. 
