# SUMMARY

In this exercise, you're developing the single page application described in the requirements for the previous exercises.

The product owner has provided the minimum viable product (MVP) requirements below for the user interface. 
Your team lead has provided a (condensed) functional specification and notes for you.

This is an Ember.js application that, for intervie purposes, you'll be developing the application in an online IDE. 
(Don't worry if you've never used Ember before. The purpose is to test your problem solving 
and how you work with the team, not your Ember expertise.)

# NOTES FROM YOUR TEAM LEAD
 * You're developing this application in an online editor called Twiddle.
   * In Twiddle, if you use File > Add, the component JS files are created using syntax for “Native Components”. The examples in this application and the Ember guides use “Classic Component” syntax. You may create components to use “Classic Component” syntax. 
 * Running Tests in Twiddle:
   * The "Run Tests" button in Twiddle doesn't work, so because TDD is difficult in this interface, new tests aren't required.
   * To run tests in Twiddle: Update twiddle.json.  
     * Set “options.enable-testing” to true. 
     * Set “ENV.environment” to “test”. (When "development", the dev mock data will be loaded an interfere with test data.)
 * If you are familiar with Ember development, it’s useful to you to know: 
   * In Twiddle, the environment.js file is not used. All ENV values, including “environment” have to be set in twiddle.json. 
   * This application uses the conventional structure, not the pods structure.
 * Mocks:
   * The application mocks HTTP requests with Mirage.  
   * The mocks are fully complete to meet the spec. You should not need to modify the mock data in the “mirage” directory.  
   * Mirage has been configured to output API requests and responses to the console.  
 * The PO has seen and approved the "Home”, "Airports", and “About” screen content. 
 * All tests must pass when done.

# MVP REQUIREMENTS

## Done
 * The application SHALL have a title in h1 tag with text “Flight Tracker”. 
 * The Home screen SHALL have welcome text and images. 
 * The airports screen SHALL have a list of airports.
   Clicking on an airport from the list SHALL navigate to the airport item screen. 
 * Airport item screen SHALL include: 
   * H2 tag with airport name 
   * Airport details 
   * A list of departing flights 
   * A list of arriving flights 
 * The About screen has have a description and image about the application.

## To-Do/In Progress
 * The application SHALL have navigation links below the title to: 
    * “Home” 
    * “Airports”  
    * “Flights” 
    * “About” 
 * All pages linked from the navigation SHALL have an h2 tag with text that matches the text in the navigation.  
 * The flight screen SHALL show a list of flights. 
   Clicking on a flight from the list SHALL navigate to the flight item screen.  
 * Flight item screen SHALL include: 
   * H2 tag with flight number 
   * Flight details 
   * A list of the passengers on the flight 
 * In any lists or references to the item throughout the application: 
   * Airports SHALL display as “[Image] [Airport Name] ([IATA])”. 
   * Flights SHALL display as “[Number]: [Origin IATA] to [Destination IATA]”. 
   * Passengers SHALL display as “[First Name] [Last Name]”. 


# FUNCTIONAL SPEC

## General

 * The UI is developed using the Ember.js framework version 3.8. 
   * Ember Docs - https://api.emberjs.com/ember/3.8 
   * Ember Data Docs - https://api.emberjs.com/ember-data/3.8 
   * Ember Guides - https://guides.emberjs.com/v3.8.0/ 
 * The UI is styled using Bootstrap 3 https://getbootstrap.com/docs/3.3/css/ 
 * Uses a RESTful API using the JSON:API data format. - JSON:API Spec https://jsonapi.org/ 
 * The Ember application will use Ember Data to request and normalize the data.  
 * Since the API meets the JSON:API spec serializing and normalizing the data is handled out of the box. 
 * Each entity has its own UUID as an identifier.


## Endpoints

### /airports

HTTP Method: GET

Query Parameters: None

Response Body:

Same as /airports/:id, but returns an array of airport objects in "data" per JSON:API spec.

Example:

```
{
  "data": [
    {
      "type": "airport",
      "id": "333a7566-f036-4b62-a90e-18b9a7421400",
      "attributes": {
        "name": "Los Angeles International",
        "icao": "KLAX",
        "iata": "LAX"
      }
    }
  ]
}
```


### /airports/:id

```
{
  "data": {
    "type": "airport",
    "id": "333a7566-f036-4b62-a90e-18b9a7421400",
    "attributes": {
      "name": "Los Angeles International",
      "icao": "KLAX",
      "iata": "LAX"
    }
  }
}
```

### /flights

HTTP Method: GET

Query Parameters: 

* origin_id: ID of the origin airport
* destination_id: ID of the destination airport

Reponse Body:

Same as /flights/:id, but returns an array of flight objects in "data" per JSON:API spec.

### /flights/:id

HTTP Method: GET

Query Parameters: None

Response Body:

```
{
  "data": {
    "type": "flight",
    "id": "cec71818-ab6f-4fdd-ba2f-2bef3bad9a25",
    "attributes": {
      "number": "123",
      "departure_time": "2021-08-28T01:26:00Z",
      "arrival_time": "2021-08-28T12:18:00Z"
    },
    "relationships": {
      "origin": {
        "data": {
          "type": "airport",
          "id": "ddea88bb-50bc-4300-8a60-da99aa81e9bf"
        }
      },
      "destination": {
        "data": {
          "type": "airport",
          "id": "5355f68f-c147-4511-8a63-eb812873c8d0"
        }
      }
    }
  },
  "included": [
    {
      "type": "airport",
      "id": "ddea88bb-50bc-4300-8a60-da99aa81e9bf",
      "attributes": {
        "name": "Airport 1",
        "icao": "KABC",
        "iata": "ABC"
      }
    },
    {
      "type": "airport",
      "id": "5355f68f-c147-4511-8a63-eb812873c8d0",
      "attributes": {
        "name": "Airport 2",
        "icao": "KXYZ",
        "iata": "XYZ"
      }
    }
  ]
}
```

### /passengers

HTTP Method: GET

Query Parameters:

* flight_id: The ID for a single flight to obtain passengers for.

Response Body:

Same as /passenger/:id, but returns an array of passenger objects in "data" per JSON:API spec.

### /passengers/:id

HTTP Method: GET

Query Parameters: None

Response Body:

```
{
  "data": {
    "type": "passenger",
    "id": "5dcaa83e-f214-4dc2-a2cb-5599287f517b",
    "attributes": {
      "first_name": "Joe",
      "last_name": "Smith"
    },
    "relationships": {
      "flight": {
        "data": {
          "type": "flight",
          "id": "cec71818-ab6f-4fdd-ba2f-2bef3bad9a25"
        }
      }
    }
  },
  "included": [
    {
      "type": "flight",
      "id": "cec71818-ab6f-4fdd-ba2f-2bef3bad9a25",
      "attributes": {
        "number": "123",
        "departure_time": "2021-08-28T01:26:00Z",
        "arrival_time": "2021-08-28T12:18:00Z"
      }
    }
  ]
}
```


