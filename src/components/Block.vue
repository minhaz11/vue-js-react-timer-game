<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click Me
    </div>
</template>

<script>
    export default {
        props:['delay'],
        data() {
            return {
                showBlock : false,
                timer : null,
                reactTimer : 0
            }
        },

        mounted() {
            setTimeout(()=> {
                this.showBlock = true,
                this.startTimer();
            }, this.delay)
        },

        methods: {
            startTimer () {
                this.timer = setInterval(() => {
                    this.reactTimer += 10; 
                },10)
            },
            stopTimer () {
                clearInterval(this.timer)
                this.showBlock = false,
                this.$emit('end',this.reactTimer)
            }
        },
    }
</script>

<style scoped>
    .block{
        padding: 100px 0;
        margin: 40px auto;
        background:  rgb(55, 131, 59);
        color: white;
        text-align: center;
        border-radius: 3px;
    }
</style>