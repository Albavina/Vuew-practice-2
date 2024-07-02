<!-- TEMPLATE 
    - This is the content we will see. 
    - We write it in HTML-->
<template>
    <div class="App">
    
            <h1>Picture time! 📸</h1>

            <!-- We add the components below: -->
            <Form @submitted="addImage"/>
            <Content :images="images"/>
            
        </div>
</template>
    
<!-- SCRIPTS 
    - These will add data and functionality to our app.
    - We write them in Javascript. -->
<script>
    // import component (by file path)
    import Form from "./components/Form.vue"
    import Content from "./components/Content.vue"

    export default {
        //  The name of our component. It should match the file name.
        name: 'App',
        // This is where we list any components we import.
        components: {
            Form,
            Content
        },
        // This is where we create variables (in the return statement)
        data() {
            return {
                // Add variables to save url from input, and to save all image urls together
                
                images:[],
              
            }
        },
        // This is where we define our functions.
        methods: {
            addImage(receivedUrl) {
                // push image url into the images array. It is not this.url because now we take the url from the Form component:
                this.images.push(receivedUrl);
            //We do not move the whole method into the Form component because we will need this method in other components too so it must be in the first common ancestor which in this case is the App.vue
            },
            // toggle isBig true or false
            
        }
    }
</script>
    
<!-- STYLES
    - These will add style and formatting to our content.
    - We write it in CSS -->
<style>
    .App {
        margin: 0 auto;
        font-family: Arial, Helvetica, sans-serif;
        text-align: center;
    }

    input, button {
        margin-bottom: 2em;
    }

    button {
        border-radius: 5px
    }

    .image-grid {
        /* set it up as a grid with 3 columns, and a gap between images */
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 1em;
        
        /* center it on the page */
        width: 50%;
        margin: auto;
    }

    img {
        /* standardize height */
        height: 150px;
        /* make everything square */
        aspect-ratio: 1;
        /* make sure image is cropped, not distorted */
        object-fit: cover;
        /* round the corners */
        border-radius: 10%;
    }

    /* Create "active" class */
    .active {
        color: red;
        border: 2px solid red;
    }

    /* Create "big" class */
    .big {
        height: 200px;
    }

    .component{
    border: 1px solid black;
    border-radius: 10px;
    margin: 1em;
    }
</style>