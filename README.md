# mbta-api-queries

# 🚀 Query the MBTA v3 API via curl 🚀

https://github.com/coding-to-music/mbta-api-queries


From / By 
## Environment variables:

```java

```

## GitHub

```java
git init
git add .
git remote remove origin
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:coding-to-music/mbta-api-queries.git
git push -u origin main
```

## Swagger API Documentation

https://api-v3.mbta.com/docs/swagger/index.html


## Goal

Service:

- Commuter Rail
- Bus
- Train
- Commuter Rail

Interesting Attributes

- Short Name
- Long Name
- Color of Line
- Color of Text
- Sort Order

Interesting Content

- Stops
- Service Alerts


## Examples of using filter and the key api endpoints

```
  const requestURL = `${REQUEST_DOMAIN}/predictions/?filter[route]=${routeId}&filter[stop]=${routeStopId}&sort=direction_id,departure_time`;
  const requestURL = `${REQUEST_DOMAIN}/routes/?sort=type,short_name,long_name,description`;
  const requestURL = `${REQUEST_DOMAIN}/schedules/?filter[route]=${routeId}&filter[stop]=${routeStopId}&sort=direction_id,departure_time`;
  const requestURL = `${REQUEST_DOMAIN}/stops/?filter[route]=${routeId}&sort=name`;
  const requestURL = `${REQUEST_DOMAIN}/alerts/?filter[route]=${routeId}&sort=-severity`;

    "id": "Green-C",
```

```
  const requestURL = `${REQUEST_DOMAIN}/stops/?filter[route]=${routeId}&sort=name`;
```

# all stops in the system

```
curl -X GET "https://api-v3.mbta.com/stops" -H "accept: application/vnd.api+json" | jq | more 
```

# all stops for a particular route

```
curl -X GET "https://api-v3.mbta.com/stops/?filter[route]=Green-C&sort=name" -H "accept: application/vnd.api+json" | jq | more 
```

# all stops for a particular route, returning the address field
curl -X GET "https://api-v3.mbta.com/stops/?filter[route]=Green-C&sort=name&fields[stop]=address" -H "accept: application/vnd.api+json" | jq | more 

# all stops for a particular route, returning the address, name and municipality fields
curl -X GET "https://api-v3.mbta.com/stops/?filter[route]=Green-C&sort=name&fields[stop]=address,name,municipality" -H "accept: application/vnd.api+json" | jq | more

# include the predicted next arrival time at each stop -- get output "Unsupported include(s): predictions"
```
curl -X GET "https://api-v3.mbta.com/stops/?filter[route]=Green-C&sort=name&include=predictions&fields[stop]=address,name,municipality&fields[prediction]=arrival_time" -H "accept: application/vnd.api+json" | jq | more
```


```
curl -X GET "https://api-v3.mbta.com/predictions/?filter[route]=Green-C&filter[stop]=${routeStopId}&sort=direction_id,departure_time" -H "accept: application/vnd.api+json" | jq | more 

curl -X GET "https://api-v3.mbta.com/stops/?filter[route]=Green-C&fields[trip]=address" -H "accept: application/vnd.api+json" | jq | more 

curl -X GET "https://api-v3.mbta.com/route_patterns?filter[route]=Green-C&include=representative_trip&fields[trip]=headsign" -H "accept: application/vnd.api+json" | jq | more
```
# ###################################
# Goals
# ###################################

## Get list of lines

```
curl -X GET "https://api-v3.mbta.com/lines" -H "accept: application/vnd.api+json" | jq | more

curl -X GET "https://api-v3.mbta.com/lines" -H "accept: application/vnd.api+json" | jq | grep long_name | more
```

## Get Routes on each line

```
  const requestURL = `${REQUEST_DOMAIN}/routes/?sort=type,short_name,long_name,description`;

curl -X GET "https://api-v3.mbta.com/routes/?sort=type,short_name,long_name,description" -H "accept: application/vnd.api+json" | jq | more

curl -X GET "https://api-v3.mbta.com/routes/?sort=type,short_name,long_name,description" -H "accept: application/vnd.api+json" | jq | grep long_name | more

```

## Get Stops on a Route

```
curl -X GET "https://api-v3.mbta.com/stops/?filter[route]=Green-C&sort=name" -H "accept: application/vnd.api+json" | jq | more 
```
# all stops for a particular route, returning the address, name and municipality fields
curl -X GET "https://api-v3.mbta.com/stops/?filter[route]=Green-C&sort=name&fields[stop]=address,name,municipality" -H "accept: application/vnd.api+json" | jq | more


## Get running equipment on each Route

```
```

## Get Prediction for a stop

```
```


# ###################################
# General Research Queries
# ###################################

### Get Lines

```
curl -X GET "https://api-v3.mbta.com/lines" -H "accept: application/vnd.api+json" | jq | more

curl -X GET "https://api-v3.mbta.com/lines" -H "accept: application/vnd.api+json" | jq | grep long_name | more
```

Interesting fields

```
id
color
long_name
short_name
text_color
```

```
    {
      "attributes": {
        "color": "00843D",
        "long_name": "Green Line",
        "short_name": "",
        "sort_order": 10032,
        "text_color": "FFFFFF"
      },
      "id": "line-Green",
      "links": {
        "self": "/lines/line-Green"
      },
      "type": "line"
    },
```

    "id": "line-Red",

### Get Stops

```
curl -X GET "https://api-v3.mbta.com/stops/" -H "accept: application/vnd.api+json" | jq | more

curl -X GET "https://api-v3.mbta.com/stops/?filter[route]=${routeId}&sort=name" -H "accept: application/vnd.api+json"
```

## Examples 

```
  const requestURL = `${REQUEST_DOMAIN}/predictions/?filter[route]=${routeId}&filter[stop]=${routeStopId}&sort=direction_id,departure_time`;
  const requestURL = `${REQUEST_DOMAIN}/routes/?sort=type,short_name,long_name,description`;
  const requestURL = `${REQUEST_DOMAIN}/schedules/?filter[route]=${routeId}&filter[stop]=${routeStopId}&sort=direction_id,departure_time`;
  const requestURL = `${REQUEST_DOMAIN}/stops/?filter[route]=${routeId}&sort=name`;
  const requestURL = `${REQUEST_DOMAIN}/alerts/?filter[route]=${routeId}&sort=-severity`;
```

```
curl -X GET "https://api-v3.mbta.com/stops/" -H "accept: application/vnd.api+json" | jq | grep Coolidge | more
```

```
        "name": "Brighton St @ Coolidge Rd",
        "at_street": "Coolidge Avenue",
        "name": "Mt Auburn St opp Coolidge Ave",
        "at_street": "Coolidge Street",
        "name": "Harvard St @ Coolidge St",
        "at_street": "Coolidge Street",
        "name": "Ferry St @ Coolidge St",
        "description": "Coolidge Corner - Green Line - (C) Cleveland Circle",
        "name": "Coolidge Corner",
        "at_street": "Coolidge Road",
        "description": "Coolidge Corner - Green Line - Park Street & North",
        "name": "Coolidge Corner",
        "at_street": "Coolidge Avenue",
        "name": "Mt Auburn St @ Coolidge Ave",
        "at_street": "Coolidge Road",
        "name": "N Harvard St @ Coolidge Rd",
        "at_street": "Coolidge Street",
        "name": "Harvard St @ Coolidge St",
        "at_street": "Coolidge Road",
        "name": "Spring Rd @ Coolidge Rd",
        "at_street": "Coolidge Avenue",
        "name": "Lynn St @ Coolidge Ave",
        "at_street": "Coolidge Street",
        "name": "Washington St @ Coolidge Rd",
        "name": "Coolidge Corner",
```

```
        "self": "/lines/line-Green"

curl -X GET "https://api-v3.mbta.com/lines" -H "accept: application/vnd.api+json" | jq | more 

curl -X GET "https://api-v3.mbta.com/lines/line-Green" -H "accept: application/vnd.api+json" | jq | more 
curl -X GET "https://api-v3.mbta.com/lines/line-Red" -H "accept: application/vnd.api+json" | jq | more 
curl -X GET "https://api-v3.mbta.com/lines/line-Blue" -H "accept: application/vnd.api+json" | jq | more 
curl -X GET "https://api-v3.mbta.com/lines/line-Orange" -H "accept: application/vnd.api+json" | jq | more 

curl -X GET "https://api-v3.mbta.com/lines/line-Blue/stops/" -H "accept: application/vnd.api+json" | jq | more 


curl -X GET "https://api-v3.mbta.com/stops" -H "accept: application/vnd.api+json" | jq | more 

curl -X GET "https://api-v3.mbta.com/stops" -H "accept: application/vnd.api+json" | jq | grep self | more 

curl -X GET "https://api-v3.mbta.com/stops/" -H "accept: application/vnd.api+json" | jq | grep Coolidge | more
```

```
curl -X GET "https://api-v3.mbta.com/stops" -H "accept: application/vnd.api+json" | jq | grep Coolidge | more 
```

```
        "name": "Brighton St @ Coolidge Rd",
        "at_street": "Coolidge Avenue",
        "name": "Mt Auburn St opp Coolidge Ave",
        "at_street": "Coolidge Street",
        "name": "Harvard St @ Coolidge St",
        "at_street": "Coolidge Street",
        "name": "Ferry St @ Coolidge St",
        "description": "Coolidge Corner - Green Line - (C) Cleveland Circle",
        "name": "Coolidge Corner",
        "at_street": "Coolidge Road",
        "description": "Coolidge Corner - Green Line - Park Street & North",
        "name": "Coolidge Corner",
        "at_street": "Coolidge Avenue",
        "name": "Mt Auburn St @ Coolidge Ave",
        "at_street": "Coolidge Road",
        "name": "N Harvard St @ Coolidge Rd",
        "at_street": "Coolidge Street",
        "name": "Harvard St @ Coolidge St",
        "at_street": "Coolidge Road",
        "name": "Spring Rd @ Coolidge Rd",
        "at_street": "Coolidge Avenue",
        "name": "Lynn St @ Coolidge Ave",
        "at_street": "Coolidge Street",
        "name": "Washington St @ Coolidge Rd",
        "name": "Coolidge Corner",
```

```
curl -X GET "https://api-v3.mbta.com/stops" -H "accept: application/vnd.api+json" | jq | more 

curl -X GET "https://api-v3.mbta.com/routes" -H "accept: application/vnd.api+json" | jq | more 

curl -X GET "https://api-v3.mbta.com/routes" -H "accept: application/vnd.api+json" | jq | grep self | more 
```

```
        "self": "/routes/Red"
        "self": "/routes/Mattapan"
        "self": "/routes/Orange"
        "self": "/routes/Green-B"
        "self": "/routes/Green-C"
        "self": "/routes/Green-D"
        "self": "/routes/Green-E"
        "self": "/routes/Blue"
        "self": "/routes/741"
        "self": "/routes/742"
        "self": "/routes/743"
        "self": "/routes/751"
        "self": "/routes/749"
        "self": "/routes/746"
        "self": "/routes/CR-Fairmount"
        "self": "/routes/CR-Fitchburg"
        "self": "/routes/CR-Worcester"
        "self": "/routes/CR-Franklin"
        "self": "/routes/CR-Greenbush"
        "self": "/routes/CR-Haverhill"
        "self": "/routes/CR-Kingston"
        "self": "/routes/CR-Lowell"
        "self": "/routes/CR-Middleborough"
        "self": "/routes/CR-Needham"
        "self": "/routes/CR-Newburyport"
        "self": "/routes/CR-Providence"
        "self": "/routes/CR-Foxboro"
        "self": "/routes/Boat-F4"
        "self": "/routes/Boat-F1"
        "self": "/routes/Boat-EastBoston"
        "self": "/routes/747"
        "self": "/routes/708"
        "self": "/routes/1"
        "self": "/routes/4"
        "self": "/routes/7"
        "self": "/routes/8"
        "self": "/routes/9"
        "self": "/routes/10"
        "self": "/routes/11"
        "self": "/routes/14"
        "self": "/routes/15"
```


```
curl -X GET "https://api-v3.mbta.com/routes/Green-C" -H "accept: application/vnd.api+json" | jq | more 
```

```
{
  "data": {
    "attributes": {
      "color": "00843D",
      "description": "Rapid Transit",
      "direction_destinations": [
        "Cleveland Circle",
        "Government Center"
      ],
      "direction_names": [
        "West",
        "East"
      ],
      "fare_class": "Rapid Transit",
      "long_name": "Green Line C",
      "short_name": "C",
      "sort_order": 10033,
      "text_color": "FFFFFF",
      "type": 0
    },
    "id": "Green-C",
    "links": {
      "self": "/routes/Green-C"
    },
    "relationships": {
      "line": {
        "data": {
          "id": "line-Green",
          "type": "line"
        }
      }
    },
    "type": "route"
  },
  "jsonapi": {
    "version": "1.0"
  }
}
```


