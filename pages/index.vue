<template>
  <div>
    Cookies Per Second: {{$store.state.perSecond}}
    <br>
    Cookies owned : {{$store.state.counter}}
    <img @click="addCookie" src="../jackson.jpg">
    <button :disabled="$store.state.counter<10" @click="addPerSecond" class="button is-danger is-outlined">AUTO CLICK</button>
    <button :disabled="$store.state.counter<50" @click="addPerSecond5" class="button is-danger is-outlined">5 CLICKS(candy)</button>
    <button :disabled="$store.state.counter<100" @click="addPerSecond10" class="button is-danger is-outlined">10 CLICKS(new life)</button>
  </div>
</template>
<script>
    export default {
        mounted(){
            setInterval(()=>{
                this.$store.dispatch('increment', this.$store.state.perSecond);
            }, 1000);
        },
        methods: {
            addCookie(){
                this.$store.dispatch('increment', 1);
            },
            addPerSecond(){
                this.$store.dispatch('incrementPerSecond', 1);
                this.$store.dispatch('increment', -10);
            },
            addPerSecond5(){
                this.$store.dispatch('incrementPerSecond', 5);
                this.$store.dispatch('increment', -50);
            },
            addPerSecond10(){
                this.$store.dispatch('incrementPerSecond', 10);
                this.$store.dispatch('increment', -100);
            }
        }
    }
</script>
<style>
  img{
    height: 300px;
  }
</style>
