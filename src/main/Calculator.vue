<template>
    <div class="calculator">
        <Display :value="displayValue"></Display>
        <Button label="AC" triple @bclick="clearMemory"></Button>
        <Button label="/" operation @bclick="setOperation"></Button>
        <Button label="7" @bclick="addDigit"></Button>
        <Button label="8" @bclick="addDigit"></Button>
        <Button label="9" @bclick="addDigit"></Button>
        <Button label="*" operation @bclick="setOperation"></Button>
        <Button label="4" @bclick="addDigit"></Button>
        <Button label="5" @bclick="addDigit"></Button>
        <Button label="6" @bclick="addDigit"></Button>
        <Button label="-" operation @bclick="setOperation"></Button>
        <Button label="1" @bclick="addDigit"></Button>
        <Button label="2" @bclick="addDigit"></Button>
        <Button label="3" @bclick="addDigit"></Button>
        <Button label="+" operation @bclick="setOperation"></Button>
        <Button label="0" double @bclick="addDigit"></Button>
        <Button label="." @bclick="addDigit"></Button>
        <Button label="=" operation @bclick="setOperation"></Button>
    </div>
</template>

<script>
import Button from './../components/Button.vue'
import Display from './../components/Display.vue'
import Footer from './../components/Footer.vue'
export default {
    components: { Button, Display, Footer },
    data() {
        return {
            displayValue: '0',
            clearDisplay: false,
            operation: null,
            values: [0, 0],
            current: 0
        }
    },
    methods: {
        clearMemory() {
            Object.assign(this.$data, this.$options.data())
        },
        setOperation(operation) {
            if (this.current === 0) {
                this.operation = operation
                this.current = 1
                this.clearDisplay = true
            } else {
                const esquals = operation === '='
                const currentOperation = this.operation

                try {
                    this.values[0] = eval(
                        `${this.values[0]} ${currentOperation} ${this.values[1]}`
                    )
                } catch (error) {
                    this.$emit('onError', error)
                }

                this.values[1] = 0
                this.displayValue = this.values[0]
                this.operation = esquals ? null : operation
                this.current = esquals ? 0 : 1
                this.clearDisplay = !esquals
            }

        },
        addDigit(digit) {
            if (digit === '.' && this.displayValue.includes('.')) {
                return
            }
            const clearDisplay = this.displayValue === '0' ||
                this.clearDisplay
            const currentValue = clearDisplay ? '' : this.displayValue
            const displayValue = currentValue + digit
            this.displayValue = displayValue
            this.clearDisplay = false

            if (digit !== '.') {
                const i = this.current
                const newValue = parseFloat(displayValue)
                this.values[i] = newValue
            }
        }
    },
}
</script>

<style>
.calculator {
    height: 450px;
    width: 300px;
    border-radius: 5px;
    overflow: hidden;
    display: grid;
    grid-template-columns: repeat(4, 25%);
    grid-template-rows: 1fr 65px 65px 65px 65px 65px;

    color: #fff;
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
</style>