<template>
  <div>
    <svg id='mako'></svg>
    <div class="title">Information</div>
    <div class="items">
      <div class="item">
        <div class="name">Path:</div>
        <div class="value">{{ path }}</div>
      </div>
      <div class="item">
        <div class="name">Route Name:</div>
        <div class="value">{{ name }}</div>
      </div>
      <div class="item">
        <div class="name">Vue.js:</div>
        <div class="value">{{ vue }}</div>
      </div>
      <div class="item">
        <div class="name">Electron:</div>
        <div class="value">{{ electron }}</div>
      </div>
      <div class="item">
        <div class="name">Node:</div>
        <div class="value">{{ node }}</div>
      </div>
      <div class="item">
        <div class="name">Platform:</div>
        <div class="value">{{ platform }}</div>
      </div>
    </div>
  </div>
</template>

<script>
  import * as d3 from 'd3'

  export default {
    methods: {

      mapitUp () {
        let width = 960
        var height = 500

        let svg = d3.selectAll('#mako')

        let mapG = svg.append('g')

        // dist layer
        let showLayer = mapG.append('g')
        // water dissolve prolly not needed

        let projection = d3.geoAlbers()
          .scale(800)
          .translate([width / 2, height / 2])

        let path = d3.geoPath()
          .projection(projection)

        // im chheky using the raw source of this file in the repo
        // so I dont have to build an api ;3
        let url = 'https://raw.githubusercontent.com/davjones0/vueMap/master/src/renderer/data/mapgeo.json'
        // d3.json(postData, function (err, geojson) {
        d3.json(url, function (err, geojson) {
          if (err) {
            console.log(err)
          }
          showLayer.selectAll('path')
            .data(geojson.features)
            .enter().append('path')
            .attr('stroke', 'white')
            .attr('d', path)
        })
      }
    },
    mounted () {
      this.mapitUp()
    },
    data () {
      return {
        electron: process.versions['atom-shell'],
        name: 'renderMap',
        node: process.versions.node,
        path: '/',
        platform: require('os').platform(),
        vue: require('vue/package.json').version
      }
    }
  }
</script>

<style scoped>
  svg {
    width: 960px;
    height: 500px;
  }

  .title {
    color: #888;
    font-size: 18px;
    font-weight: initial;
    letter-spacing: .25px;
    margin-top: 10px;
  }

  .items { margin-top: 8px; }

  .item {
    display: flex;
    margin-bottom: 6px;
  }

  .item .name {
    color: #6a6a6a;
    margin-right: 6px;
  }

  .item .value {
    color: #35495e;
    font-weight: bold;
  }
</style>
