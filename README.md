# cx25 ![Original cardXchange logo](docs/history/CX_3.gif)

An AI / Vibe Coding experiment. 

## The App 

cx25 stands for _cardXchange 2025_ and is the remake of our 2001 cardXchange idea. Here is what the MVP of cx25 does (we also call this _Generation 0_).

### Generation 0

* As a user I can enter and modify my data: Name (first, middle, last), the company I work at and what position I hold, my private and professional address, my email addresses and phone numbers as well as my picture. We call this a cx-card.
* As a user I can exchange my cx-card with another cx user. By default this happens via iMessage.  We are then linked. I see the cx-cards of all the users I am linked too.
* As a user I can modify my cx-card data - and all the users that are linked to me see these changes in real time.

**Non functional / tech**

* We have an iOS app
* Data is stored in [Apple CloudKit](https://developer.apple.com/icloud/cloudkit/)

### Generation 1: Sync with Contacts

* As a user I can link the cx App to my iOS Contacts. 
* From then on my cx-card is maintained in my Contacts.
* When my linked users change their data, I can choose to update it within my contacts - or not.

Test from Philip
