# Location Finder API

This is a FastAPI-based API that helps you find nearby locations within a 50km radius from a given location. It includes functionality to correct misspelled location names using Google Gemini API and fuzzy matching with difflib for location name resolution. The API also integrates GeoPy to fetch coordinates for locations that aren't predefined in the system.

## Features

- **Location Name Normalization**: Uses Google Gemini API for correcting misspelled location names based on predefined locations.
- **Fuzzy Matching**: Uses Python's difflib to find the closest matches for location names.
- **Geocoding**: Uses GeoPy's Nominatim API to fetch coordinates for a given location.
- **Haversine Distance**: Calculates the distance between two coordinates using the Haversine formula.
- **Nearby Locations**: Returns locations within a 50km radius from the provided location name.

## Predefined Locations

The API has a list of predefined locations with their respective latitude and longitude. If the user provides a location name, the system attempts to find the closest match from this list. If no match is found, the system attempts to geocode the location.

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/location-finder-api.git
    cd location-finder-api
    ```

2. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

3. Add your Google Gemini API key in the `main.py` file:
    ```python
    GEMINI_API_KEY = "your_api_key_here"
    ```

4. Run the FastAPI server:
    ```bash
    uvicorn main:app --reload
    ```

## Endpoints

### `/nearby-locations`
- **Method**: `GET`
- **Description**: Finds locations within a 50km radius of the given location.
- **Query Parameters**:
  - `query`: The name of the location (e.g., "Udaipur").
- **Response**:
    - Returns a JSON object containing the coordinates of the query location and nearby locations within a 50km radius.

Example:
```bash
GET /nearby-locations?query=Udaipur
