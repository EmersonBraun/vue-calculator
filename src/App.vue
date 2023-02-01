<template>
    <div id="app">
        <Calculator></Calculator>
        <Footer />
    </div>
</template>

<script>
import Calculator from './main/Calculator.vue'
import Footer from './components/Footer.vue'
export default {
    components: { Calculator, Footer }
}
</script>

<style scoped>
#app {
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
    align-items: center;
    text-align: center;
    color: #fff;
    background: linear-gradient(to right, rgb(83, 105, 118), rgb(41, 46, 73))
}
</style>