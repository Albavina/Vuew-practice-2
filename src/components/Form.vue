<template>
    <div class="component">
         <!-- INPUT FORM -->
            <!-- button with @click to toggle showForm -->
            <button @click="showForm = !showForm">
                <!-- Conditionally change button text: if form is showing, button should say "Hide form" -->
                <p v-if="showForm">Hide form 🙈</p>
                <!-- Else (if form is hidden), should say "Add images!" -->
                <p v-else>Add images! 🖼️</p>
            </button>
            <!-- Add v-if to form, so it only renders when "showForm" is true -->
            <form v-if="showForm">
                Add image: 
                <!-- Add v-model to save input as a variable in data -->
                <input type="text" v-model="url"/>
                <br />
                <!-- Add @click event handler. ".prevent" to prevent the page refreshing. -->
                <button @click.prevent="handleSubmit">Submit</button>
            </form>

    </div>
  
</template>

<script>
export default {
    name: "Form",
    props: [],
    components: {},
    data (){
        return {
            url: "",
            showForm: false,
        }
    },
    methods: {
        handleSubmit(){
            //emit the url to the parent App.vue ("submitted" is an arbitrary name we give to the action. We have to call this name in the App.vue):
            this.$emit("submitted", this.url)
             // reset the form to blank
             this.url = "";
        }
    }
}
</script>

<style>

</style>