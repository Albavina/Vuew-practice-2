<template>
<!-- IMAGE GRID PORTION-->
<div class="component">
            <!-- BIG & SMALL BUTTONS -->
    <div class = "buttons">
        <!-- Add click handlers to toggle "isBig" data -->
        <!-- Add conditional class "active": for Big when "isBig" is true, for Small when false -->
        <button @click="toggle(true)" :class="{ active: isBig }">Big</button>
        <button @click="toggle(false)" :class="{ active: !isBig }">Small</button>
    </div>
             <!-- IMAGES -->
    <div class = "image-grid">
                <!-- Create an <img> tag for each of your URLs using a v-for loop. Set your URL as the src attribute. -->
                <!-- Add conditional class "big" when "isBig" is true -->
      <img 
             v-for="(url, index) in images" 
            :key = "index"
            :src = "url"
            :class="{ big: isBig }"
            @click="handleClick(url)"
        />
    </div>
  </div>
</template>

<script>
export default {
    name: "ImageGrid",
    props: ["images"],
    components: {},
    data (){
        return {
          isBig : false
          //We create this variable to storage the url that comes from the ImageGrid component so then we can have access to it from the Featured component.
        }
    },
    methods: {
      toggle(state) {
                this.isBig = state
            },

      handleClick(url){
        this.$emit("clicked", url);

      }

    }

}
</script>

<style>

</style>