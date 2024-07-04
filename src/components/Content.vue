<template>
     
    <div class="component">
        <h3>Content</h3>
        <Featured 
        :featured="featured"
        v-if="featured"
        />
        <!-- This conditional is only to show a picture on the feature box only if there is an image selected  -->
        <ImageGrid
         :images="images"
         @clicked="setFeatured"/>
    </div>
  
</template>

<script>
import ImageGrid from "./ImageGrid.vue"
import Featured from "./Featured.vue"

export default {
    name: "Content",
    props: ["images"],
    components: {
        ImageGrid,
        Featured
    },
    data (){
        return {
            featured: null
        }
    },
    methods: {
        setFeatured(url){
            this.featured = url
            //This will update the variable featured created in data above.
        }

    }

}
</script>

<style>


</style>