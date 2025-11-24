# Updated "Visited Places" Map

A standalone web application for visualizing countries and cities you have visited during your travels. This fork includes enhanced features like visited options (see below), high-resolution maps, and improved interactivity.

## Features

* **Standalone HTML+JavaScript webapp** - No backend required, works entirely offline
* **No external dependencies** - All libraries (D3.js and Datamaps) are included locally
* **High-resolution world map** - Uses detailed map data for better visualization
* **Interactive zoom and pan** - Zoom in/out (1x to 10x) and pan around the map
* **Constant-size city markers** - City dots maintain their size when zooming for better visibility
* **Multiple visit categories**:
  - **Countries**: Visited, Planning
  - **Cities**: Lived (>3 months), Stayed (>1 week), Visited, Passed through, Planning
* **Hover tooltips** - Shows city name and date when hovering over markers
* **Color-coded legend** - Visual guide for all visit categories
* **Responsive design** - Adapts to window resizing

## How to Use

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd visited_places
   ```

2. **Set up your data files**
   - Change `cities_example.js` to `cities.js` (remove `_example` from filename)
   - Change `countries_example.js` to `countries.js` (remove `_example` from filename)

3. **Edit your data**
   - **Countries**: Use ISO alpha-3 country codes (e.g., `CHN` for China, `GBR` for United Kingdom)
      * Refer to websites like [Country Codes Alpha-2 & Alpha-3](https://www.iban.com/country-codes) for a complete list
   - **Cities**: Add cities with latitude, longitude, and appropriate `fillKey` category
   - See the example files for the exact format

4. **Open in browser**
   - Simply open `index.html` in your web browser
   - Use mouse wheel to zoom, click and drag to pan

## File Structure

```
visited_places/
├── index.html              # Main HTML file
├── cities_example.js       # Example city data (copy to cities.js)
├── countries_example.js     # Example country data (copy to countries.js)
├── cities.js               # Your personal city data (gitignored)
├── countries.js            # Your personal country data (gitignored)
├── d3/                     # D3.js library files
│   ├── d3.v3.min.js
│   └── topojson.v1.min.js
└── datamaps/               # Datamaps library files
    ├── datamaps.world.min.js
    └── datamaps.world.hires.min.js
```

## Data Format

### Cities (`cities.js`)
```javascript
CITIES = [
    {name: 'City Name', latitude: 39.9042, longitude: 116.4074, 
     radius: 3, fillKey: 'city_lived', date: '2020-01', color: '#1E90FF'},
]
```

**fillKey options:**
- `city_lived` - Lived for more than 3 months (Blue)
- `city_stayed` - Stayed for more than 1 week (Green)
- `city_visited` - Visited (Red)
- `city_passed_through` - Passed through (Grey)
- `city_planning` - Planning to visit (Yellow)

### Countries (`countries.js`)
```javascript
COUNTRIES = {
    CHN: {fillKey: 'country_visited'},   // China
    GBR: {fillKey: 'country_planning'},  // United Kingdom
}
```

**fillKey options:**
- `country_visited` - Visited (Green)
- `country_planning` - Planning to visit (Yellow)

## Customization

* **Map resolution**: Edit line 7 in `index.html` - remove `hires` to use low-resolution map (not recommended)
* **Colors**: Modify the `fills` object in `index.html` (line 93-110) to change color scheme
* **Zoom levels**: Adjust `scaleExtent([1, 10])` in the zoom configuration (line 166)
* **Legend position**: Modify CSS for `.legend` class (line 39-49)
* Refer to [D3 Datamaps documentation](http://datamaps.github.io/) for advanced customization

## Privacy

Your personal data files (`cities.js` and `countries.js`) are automatically ignored by git (see `.gitignore`). This ensures your travel history stays private when sharing the repository.

## Credits

Based on D3 Datamaps examples. Original work by Paul Sokolovsky, and zoom support by Seonghyeon Moon. MIT license.
