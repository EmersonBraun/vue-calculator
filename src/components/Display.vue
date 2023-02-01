<template>
    <div class="display">
        {{ value }}
    </div>
</template>

<script>
    export default {
        props: ['value']
    }
</script>

<style scoped>
.display {
    grid-column: span 4;
    background-color: #0004;
    display: flex;
    align-items: center;
    justify-content: flex-end;
    padding: 20px;
    font-size: 2.1em;
    overflow: hidden;

    height: 100px;
    width: calc(100% - 25px);
    margin: 10px;

    background-color: #a7af7c;
    margin-bottom: 10px;
    border-radius: 10px;
    text-align: right;
    font-size: 2em;
}
</style>