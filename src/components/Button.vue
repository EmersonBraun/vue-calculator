<template>
    <button class="button" :class="{ double, triple, operation }" @click="$emit('bclick', label)">
        <i>{{ label }}</i>
    </button>
</template>

<script>
export default {
    props: {
        label: {},
        operation: { type: Boolean },
        double: { type: Boolean },
        triple: { type: Boolean }
    }
}
</script>

<style>
:root {
    --bg-button: #f0f0f0;
    --border-button: solid 1px #888;
}

.button {
    font-size: 1.4em;
    background-color: #f0f0f0;
    border-right: solid 1px #888;
    border-bottom: solid 1px #888;
    outline: none;
    color: #fff;
    position: relative;
    display: grid;
    place-items: center;
    margin: 8px;
    background: linear-gradient(180deg, #2f2f2f, #3f3f3f);
    box-shadow: inset -8px 0 8px rgba(0, 0, 0, 0.15),
        inset 0 -8px 8px rgba(0, 0, 0, 0.25), 0 0 0 2px rgba(0, 0, 0, 0.75),
        10px 20px 25px rgba(0, 0, 0, 0.4);
    user-select: none;
    cursor: pointer;
    font-weight: 400;
    border-radius: 10px;
}

.button:active {
    filter: brightness(1.5);
}

.button::before {
  content: "";
  position: absolute;
  top: 2px;
  left: 3px;
  bottom: 10px;
  right: 8px;
  border-radius: 10px;
  box-shadow: -5px -5px 15px rgba(0, 0, 0, 0.1),
    10px 5px 10px rgba(0, 0, 0, 0.15);
  border-left: 1px solid #0004;
  border-bottom: 1px solid #0004;
  border-top: 1px solid #0009;
}

.button i {
  position: relative;
  font-style: normal;
  font-size: .9em;
  text-transform: uppercase;
}

.button.double {
    grid-column: span 2;
}

.button.triple {
    grid-column: span 3;
}

.button.operation {
    background: #fa8231;
    color: #fff;
}

.button.operation:active {
    color: #fa8231cc;
}
</style>