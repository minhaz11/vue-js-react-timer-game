<template>
    <div>
       <p> Your score is {{ score }} ms</p>

        <p>You are {{ title }}</p>
    </div>
</template>

<script>
    export default {
        props:['score'],
        data() {
            return {
                title:null
            }
        },

        mounted() {
            if(this.score < 250){
                this.title = 'Super Fast';
            } else if(this.score < 400 ){
                this.title = 'Moderate';
            } else {
                 this.title = 'Lazy';
            }
          
        },
    }
</script>

<style scoped>

</style>