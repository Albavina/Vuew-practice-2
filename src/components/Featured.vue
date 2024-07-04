<template>
  <div class="component-featured">

    <img :src="featured" />

    </div>
</template>

<script>
export default {
    name: "Featured",
    props: ["featured"]
}
</script>

<style>


.component-featured > img{
  width: 300px;
  height: 300px;
  object-fit: cover;
}

</style>