# java-full-stack-assessment
Assessment exercise for the full stack Java developer position

## GOAL

Write a secured service exposing a REST API endpoints for satellite imagery product discovery:
- Design endpoints that accept Area of Interest using GeoJSON format
- Response should include satellite imagery products with their footprints and metadata in GeoJSON format
- Products should only be returned if they spatially intersect with the provided AOI

In addition, write a simple web client displaying a map. When the application is loaded it should ask the user to authenticate. Once authenticated, prompt the user to provide an AOI (Area of interest) in GeoJSON format or by drawing on the map. Use this AOI to call the API and display the returned product footprints on the map along with product information.

### IMPORTANT
- Design your own API structure - consider RESTful principles, HTTP methods, and proper response formats
- The API needs to be secured using a token obtained from a service (Keycloak or other OAuth based services), ideally using a User account
- The actual backend is a mock, **no need for a DB**. The list of products returned can be anything as long as they "make sense" geometrically.
- Display product information (name, acquisition date, provider, resolution) alongside the map footprints
- Include product thumbnails in the display (placeholder images are fine)
- Use Maven

### BONUS
- Generate the OpenAPI specs and doc page from the code
- Advanced AOI selection tools (drawing on map vs text input)

## PRODUCT DATA STRUCTURE (SAMPLE)

Your mock products should include below satellite imagery attributes:
```json
{
  "id": "product-id",
  "name": "Sentinel-2A",
  "acquisitionDate": "2024-01-15T10:30:00Z",
  "provider": "ESA",
  "resolution": "10m",
  "thumbnailUrl": "/thumbnails/product1.jpg",
  "metadata": {
    "sensor": "MSI",
    "cloudCoverage": 15
  },
  "footprint": {
    "type": "Polygon",
    "coordinates": [[[lon,lat], [lon,lat], ...]]
  }
}
```

## TIPS and links
- https://geojson.org/
- if you decide to use Keycloak https://www.keycloak.org/ also deploy a Keycloak instance using docker compose https://www.keycloak.org/server/containers
- leaflet display of geojson https://leafletjs.com/examples/geojson/
- Mock satellite data: Create realistic product names (Sentinel-2, Landsat-8, SPOT, etc.)
- Simple spatial intersection: Bounding box overlap is acceptable for mock implementation

## EVALUATION CRITERIA
The work will be evaluated against the following criteria
- the evaluator should be able to run a working solution following the README instructions
- quality of the code and good comments
- some unit testing (no need to have full code coverage, only to demonstrate the ability to write tests)
- API design demonstrates understanding of RESTful principles
- Presentation of product information with thumbnails
- Map integration shows footprints correctly linked to product information