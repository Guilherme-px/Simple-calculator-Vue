<template>
    <div class="calculator">
        <Display :value="displayValue" />
        <Button label="AC" triple @onClick="clearMemory" />
        <Button label="/" operation @onClick="setOp" />
        <Button label="7" @onClick="addDigt" />
        <Button label="8" @onClick="addDigt" />
        <Button label="9" @onClick="addDigt" />
        <Button label="*" operation @onClick="setOp" />
        <Button label="4" @onClick="addDigt" />
        <Button label="5" @onClick="addDigt" />
        <Button label="6" @onClick="addDigt" />
        <Button label="-" operation @onClick="setOp" />
        <Button label="1" @onClick="addDigt" />
        <Button label="2" @onClick="addDigt" />
        <Button label="3" @onClick="addDigt" />
        <Button label="+" operation @onClick="setOp" />
        <Button label="0" double @onClick="addDigt" />
        <Button label="." @onClick="addDigt" />
        <Button label="=" operation @onClick="setOp" />
    </div>
</template>

<script>
import Display from "../components/Display.vue"
import Button from "../components/Button.vue"

export default {
    name: "Calculator",
    components: { Display, Button },
    data: function() {
        return {
            displayValue: "0",
            clearDisplay: false,
            operation: null,
            values: [0, null],
            current: 0
        }
    },
    methods: {
        clearMemory() {
            Object.assign(this.$data, this.$options.data())
        },
        setOp(operation) {
            if(this.current === 0) {
                this.operation = operation
                this.current = 1
                this.clearDisplay = true
            } else if(this.current !== 0 && this.values[1] !== null) {
                const equals = operation === "="
                const currentOperation = this.operation

                switch (currentOperation) {
                case '+':
                    this.values[0] = this.values[0] + this.values[1]
                    break
                case '-':
                    this.values[0] = this.values[0] - this.values[1]
                    break
                case '*':
                    this.values[0] = this.values[0] * this.values[1]
                    break
                case '/':
                    this.values[0] = this.values[0] / this.values[1]
                    break
                default:
                    return
                }
                
                this.values[1] = null
                this.displayValue = this.values[0]
                this.operation = equals ? null : operation
                this.current = equals ? 0 : 1
                this.clearDisplay = !equals
            }
        },
        addDigt(num) {
            if(num === "." && this.displayValue.includes(".")) {
                return
            }

            const clearDisplay = (this.displayValue === "0" && num !== ".") || this.clearDisplay
            const currentValue = clearDisplay ? "" : this.displayValue
            const displayValue = currentValue + num

            this.displayValue = displayValue
            this.clearDisplay = false

            if(num !== ".") {
                const i = this.current
                const newValue = parseFloat(displayValue)
                this.values[i] = newValue
            }
        }
    }
}
</script>

<style>
.calculator {
    height: 365px;
    width: 290px;
    border-radius: 5px;
    overflow: hidden;

    display: grid;
    grid-template-columns: repeat(4, 25%);
    grid-template-rows: 1fr 48px 48px 48px 48px 48px;
}
</style>