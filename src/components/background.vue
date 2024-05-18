<template>
    <div class="background-container">
        <div class="background"></div>
    </div>
</template>

<script>
export default {
    name: 'Background'
}
</script>

<style scoped>
.background-container {
    display: flex;
    justify-content: center;
    /* Centers vertically in the container */
    align-items: center;
    /* Centers horizontally in the container */
    position: relative;
    width: 100%;

    color: #000;
    /* Ensure this matches your design */
}
.background {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgb(238, 238, 238);
    z-index: -2;
}
</style>
