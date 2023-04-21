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
curl -X GET "https://api-v3.mbta.com/lines" -H "accept: application/vnd.api+json"
```
