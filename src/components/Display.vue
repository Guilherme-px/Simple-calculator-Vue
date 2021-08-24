<template>
    <div class="display">{{ value }}</div>
</template>

<script>
export default {
    name: 'Display',
    props: ['value']
}
</script>

<style>
.display {
    grid-column: span 4;
    background-color: #0004;

    display: flex;
    align-items: center;
    justify-content: flex-end;
    padding: 20px;
    font-size: 2rem;
    overflow: hidden;
}
</style>