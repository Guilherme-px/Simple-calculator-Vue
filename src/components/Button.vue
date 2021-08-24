<template>
    <button class="button" :class="{ double, triple, operation }"
        @click="$emit('onClick', label)">{{ label }}</button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        label: {},
        operation: { type: Boolean},
        double: { type: Boolean },
        triple: { type: Boolean }
    }
}
</script>

<style>
:root {
    --bg-button: #f0f0f0;
    --bg-border: solid 1px #000;
}

.button {
    font-size: 1.4rem;
    background-color: var(--bg-button);
    border: none;
    border-right: var(--bg-border);
    border-bottom: var(--bg-border);
    outline: none;
}

.button:active {
    opacity: 0.7;
}

.button.double {
    grid-column: span 2;
}

.button.triple {
    grid-column: span 3;
}

.button.operation {
    background-color: rgb(0, 0, 0, 0.5);
    color: #f0f0f0;
}
</style>