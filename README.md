# mbta-api-grafana

# 🚀 Call the MBTA v3 API via Grafana 🚀

https://github.com/coding-to-music/mbta-api-grafana


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
git remote add origin git@github.com:coding-to-music/mbta-api-grafana.git
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

## Examples 

```
  const requestURL = `${REQUEST_DOMAIN}/predictions/?filter[route]=${routeId}&filter[stop]=${routeStopId}&sort=direction_id,departure_time`;
  const requestURL = `${REQUEST_DOMAIN}/routes/?sort=type,short_name,long_name,description`;
  const requestURL = `${REQUEST_DOMAIN}/schedules/?filter[route]=${routeId}&filter[stop]=${routeStopId}&sort=direction_id,departure_time`;
  const requestURL = `${REQUEST_DOMAIN}/stops/?filter[route]=${routeId}&sort=name`;
  const requestURL = `${REQUEST_DOMAIN}/alerts/?filter[route]=${routeId}&sort=-severity`;
```

### Get Lines

```
curl -X GET "https://api-v3.mbta.com/lines" -H "accept: application/vnd.api+json"
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
    },```
```
    "id": "line-Red",

```

Output

```

```

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

```
