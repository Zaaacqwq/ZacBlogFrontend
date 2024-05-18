<template>
    <div class="imgs">
        <ul>
            <li class="item" v-for="carousel in carouselList" :key="carousel.id" :style="{
                'background-image': 'url(' + carousel.imgUrl + ')'
            }">
            </li>
        </ul>
    </div>
</template>

<script>
import { ref, onMounted } from '@vue/composition-api';

export default {
    setup() {
        const carouselList = ref([
            { id: 1, imgUrl: require('../../static/img/image1.jpg') },
            { id: 2, imgUrl: require('../../static/img/image2.jpg') },
            // { id: 3, imgUrl: require('../../static/img/image1.jpg') },
            // { id: 4, imgUrl: require('../../static/img/image1.jpg') },
            // { id: 5, imgUrl: require('../../static/img/image1.jpg') }
        ]);

        onMounted(() => {
            // Logic to execute on mount
        });

        return { carouselList };
    }
};
</script>

<style scoped>
.imgs {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 70vh;
    z-index: -1; /* Higher than the background */
    background-color: #363636;
    overflow: hidden;
}

.item {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    width: 100%;
    height: 100%;
    background: no-repeat center center / cover;
    opacity: 0;
    animation: imageAnimation 36s linear infinite;
    backface-visibility: hidden;
    transform-style: preserve-3d;
}

.item:nth-child(2) {
    animation-delay: 6s;
}

.item:nth-child(3) {
    animation-delay: 12s;
}

.item:nth-child(4) {
    animation-delay: 18s;
}

.item:nth-child(5) {
    animation-delay: 24s;
}

.item:nth-child(6) {
    animation-delay: 30s;
}

.imgs::before {
    content: '';
    display: block;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.2);
    transition: all 0.2s ease-in-out;
}

@keyframes imageAnimation {
    0% {
        opacity: 0;
        animation-timing-function: ease-in;
    }

    2% {
        opacity: 1;
    }

    8% {
        opacity: 1;
        transform: scale(1.05);
        animation-timing-function: ease-out;
    }

    17% {
        opacity: 1;
        transform: scale(1.1);
    }

    25% {
        opacity: 0;
        transform: scale(1.1);
    }

    100% {
        opacity: 0;
    }
}
</style>
