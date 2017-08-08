# vuemap

> An electron-vue mapping project showing both 2d and 3d visualizations.
> Using d3 to create maps, three.js for extruding the map geometries, d3-threeD.js to convert svg paths to three.js paths, state geometries provided by 
> U.S. census shape files converted to geojsons using mapshaper.com with 2016 average wage and labor hours data baked into the geojson using qgis.
> Also using geojson-polyline to dramatically reduce the geojson to 1/3 of it's original size by utilizing google's encoded polyline algorithm  

#### Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:9080
npm run dev

# build electron application for production
npm run build

# run unit & end-to-end tests
npm test


# lint all JS/Vue component files in `src/`
npm run lint

```

---

This project was generated with [electron-vue](https://github.com/SimulatedGREG/electron-vue)@[b31b441](https://github.com/SimulatedGREG/electron-vue/tree/b31b44123ad42acac12337c4955df4ead853f0df) using [vue-cli](https://github.com/vuejs/vue-cli). Documentation about the original structure can be found [here](https://simulatedgreg.gitbooks.io/electron-vue/content/index.html).
