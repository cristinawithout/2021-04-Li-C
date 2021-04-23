# SUMMARY

In this exercise, you're designing the database schema for a single page application that handles flight and passenger information. (Note: You do not need to worry about user authentication or managing user data.) 

Your requirements and the task are described below.

Make use of any resources available to you, including any internet search tools or documentation sites.

# REQUIREMENTS 

* The application SHALL have the following sections: 
  * Flights – A list of flights. 
    * Details for each flight contain: 
      * Number – The fight designator 
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
* Passenger data SHALL be populated from another application and must be stored locally. 
* Passenger data SHALL be read-only.
 
# TASK
 
* Design the relational database for the flight, airport, and passenger data.  
* Write the SQL query to get all passengers for a specific flight. 
* Write the SQL query to get all flights leaving a specific airport on a specific date. 
