<template>
  <div class="google-map" :id="mapName"></div>
</template>

<script>
export default {
  name: "google-map",
  props: {
    name: String,
    block: Object,
  },
  data: function() {
    return {
      mapName: this.name + "-map",
      map: null,
      bounds: null,
      markers: [],
      mc: null,
      mcOption: {
        imagePath: "src/images/m",
        width: 53,
        height: 53
      }
    };
  },
  mounted: function() {
    this.bounds = new google.maps.LatLngBounds();
    const element = document.getElementById(this.mapName);
    const mapCentre = this.block[0].location[0];
    const options = {
      center: new google.maps.LatLng(mapCentre.latitude, mapCentre.longitude)
    };
    this.map = new google.maps.Map(element, options);
    this.block.forEach(gloc => {
      const position = new google.maps.LatLng(
        gloc.location[0].latitude,
        gloc.location[0].longitude
      );
      const marker = new google.maps.Marker({
        position,
        map: this.map,
        icon: {
          url: gloc.clogo,
          scaledSize: new google.maps.Size(116, 116)
        }
      });
      this.markers.push(marker);
      this.map.fitBounds(this.bounds.extend(position));
    });
    this.mc = new MarkerClusterer(this.map, this.markers, this.mcOption);
    
  }
};
</script>

<style scoped>
.google-map {
  width: 100%;
  height: 600px;
  margin: 0 auto;
  background: gray;
}
</style>
