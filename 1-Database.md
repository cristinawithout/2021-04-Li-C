# SUMMARY

In this exercise, you're designing the database schema for a single page application that handles flight and passenger information. Your requirements and the task are described below. (Note: You do not need to worry about user authentication or managing user data.)

The interviewers are your product owner and your team lead. Ask them questions as you would if you were working with your team. You're encouraged to verbalize your thought process as you work.

Make use of any resources available to you, including any internet search tools or documentation sites.

# REQUIREMENTS 

* The application SHALL have the following sections: 
  * Flights – A list of flights. 
    * Details for each flight contain: 
      * Number – The flight designator 
      * Origin airport – The airport from which the flight will leave 
      * Destination airport – The airport to which the flight will arrive 
      * Departure date 
      * Arrival date 
      * Passengers – Passenger data consists of First Name, Last Name, and Flight 
  * Airports – A list of airports. 
    * Detail for each airport contain: 
      * Name 
      * ICAO – A 4-character code assigned by the International Civil Aviation Org. 
      *  IATA – A 3-character code assigned by the International Air Transport Assoc. 
* Each section SHALL have a screen with a list of items.  
* Clicking on an item from the list SHALL navigate to a page with detail about the item. 
* Users SHALL be able to read, create, update and delete each item. 
* Each passenger belongs to only 1 flight. Passenger data SHALL be populated from another application and must also be stored locally. Passenger data SHALL be read-only.
 
# TASK
 
* Design the relational database for the flight, airport, and passenger data.
* How would your design change if each passenger can belong to multiple flights?
* Write the SQL query to get all passengers for a specific flight. 
* Write the SQL query to get all flights leaving a specific airport on a specific date. 
