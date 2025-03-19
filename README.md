# google_maps_route_optimiser

This is a Google Maps Route Optimiser that takes in an address, translates to coordinates via an API and then calculates the distance between the coordinates before generating a Google Maps URL.

## Overview

Route Optimizer allows users to:
- Input a starting point and multiple stops to visit
- Optionally specify a fixed final destination
- Generate an optimized route using the nearest neighbor algorithm
- View the route on Google Maps with a single click

## Features

- Address to geographic coordinate conversion using Mapbox Geocoding API
- Route optimization using the nearest neighbor algorithm
- Automatic Google Maps URL generation for navigation
- Support for fixed final destinations regardless of distance
- User-friendly web interface

## Installation

### Prerequisites

- Python 3.6+
- pip (Python package installer)

### Setup

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/route-optimizer.git
   cd route-optimizer
   ```

2. Create and activate a virtual environment:
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```
   pip install -r requirements.txt
   ```

4. Create a `.env` file with your Mapbox API key:
   ```
   MAPBOX_ACCESS_TOKEN=your_mapbox_api_key_here
   ```

## Running the Application

Start the application with:

```
python app.py
```

By default, the application will run on http://0.0.0.0:5000

You can configure the host, port, and debug mode through environment variables:
- `FLASK_RUN_HOST`: Host address (default: 0.0.0.0)
- `FLASK_RUN_PORT`: Port number (default: 5000)
- `FLASK_DEBUG`: Debug mode (default: False)

## Usage

1. Enter your starting point in the first input field
2. Add stops by clicking "Add Another Stop" and entering the addresses
3. Optionally enable "Use a fixed destination" to specify a final location
4. Click "Optimize Route" to generate the most efficient path
5. View the optimized route and click "Open in Google Maps" for navigation

## Project Structure

```
route-optimizer/
├── app.py                 # Main Flask application
├── templates/
│   ├── index.html         # Form for inputting locations
│   └── route.html         # Results page showing optimized route
├── logs/
│   └── app.log            # Application log file
├── .env                   # Environment variables
└── requirements.txt       # Project dependencies
```

## How It Works

1. **Address Geocoding**: Converts addresses to geographic coordinates using Mapbox API
2. **Route Optimization**: Uses the nearest neighbor algorithm to find the shortest path
3. **Google Maps Integration**: Generates a properly formatted URL for Google Maps navigation

## Dependencies

- Flask: Web framework
- Requests: HTTP client for API communication
- GeoPy: Distance calculation between geographic coordinates
- Python-dotenv: Loading environment variables

## Configuration

Configure the application through environment variables:
- `MAPBOX_ACCESS_TOKEN`: Your Mapbox API key
- `FLASK_RUN_HOST`: Host to run the Flask app on
- `FLASK_RUN_PORT`: Port to run the Flask app on
- `FLASK_DEBUG`: Enable/disable debug mode

## Limitations

- Uses the nearest neighbor algorithm, which may not always find the globally optimal route
- Depends on external services (Mapbox for geocoding, Google Maps for routing)
- Limited to the number of waypoints supported by Google Maps (currently 23)