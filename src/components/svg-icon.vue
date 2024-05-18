<template>
    <div class="loader"></div>
</template>


<style scoped>
.loader {
    display: flex;
    align-items: center;
    justify-content: center;
}

.loader::before,
.loader::after {
    position: absolute;
    content: "";
    height: 8em;
    width: 8em;
    border: 1em solid #0060fa;
    border-radius: 50%;
    animation: loader 2s ease-out infinite;
}

.loader::after {
    opacity: 0;
    animation-delay: 2s;
}

@keyframes loader {
    0% {
        border: 1em solid #0060fa;
        transform: scale(0);
        opacity: 1;
    }

    100% {
        border: 0 solid #0060fa;
        transform: scale(1);
        opacity: 0;
    }
}
</style>
