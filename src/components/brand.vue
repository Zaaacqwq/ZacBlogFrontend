<template>
    <div ref="brandRef" class="brand-container">
        <div class="brand">
            <!-- 标题 -->
            <p class="artboard"> HelloWorld </p>
            <!-- 打字机 -->
            <div class="title">
                {{ obj.output }}
                <span class="easy-typed-cursor">|</span>
            </div>
        </div>
        <!-- 向下按钮 -->
        <button class="invisible-button" @click="scrollDown">
            <svg-icon class="arrow-down" icon-class="down" size="32px"></svg-icon>
        </button>
        <!-- 波浪 -->
        <waves></waves>
    </div>
</template>

<script>
import Wave from '../components/wave.vue';
import SvgIcon from '../components/svg-icon.vue';
import EasyTyper from "easy-typer-js";
export default {
    data() {
        return {
            obj: {
                output: "",
                isEnd: false,
                speed: 100,
                singleBack: false,
                sleep: 0,
                type: "normal",
                backSpeed: 100,
                sentencePause: false,
            },
        };
    },
    methods: {
        scrollDown() {
            window.scrollTo({
                behavior: "smooth",
                top: this.$refs.brandRef.clientHeight,
            });
        },
        fetchData() {
            fetch("https://v1.hitokoto.cn")
                .then((res) => res.json())
                .then(({ hitokoto }) => {
                    new EasyTyper(
                        this.obj,
                        hitokoto,
                        () => { },
                        () => { }
                    );
                });
        }
    },
    components: { //定义组件
        'waves': Wave,
        'svg-icon': SvgIcon,
    },
    mounted() {
        this.fetchData();
    }
}
</script>

<style scoped>
.brand-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    /* Centers vertically in the container */
    align-items: center;
    /* Centers horizontally in the container */
    position: relative;
    width: 100%;
    height: 70vh;
    min-height: 10rem;
    color: #000;
    /* Ensure this matches your design */
}

.brand {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    /* Adjusts spacing between child elements */
    align-items: center;
    /* Keeps everything centered */
    position: relative;
    /* Changed from fixed to relative */
    z-index: 1;
    /* Adjust z-index as needed */
}

.brand .artboard {
    font-family: "Fredericka the Great", Mulish, -apple-system, "PingFang SC", "Microsoft YaHei", sans-serif;
    font-size: 3.5em;
    line-height: 1.2;
    animation: titleScale 1s;
}

.brand .title {
    letter-spacing: 0.1em;
}

.easy-typed-cursor {
    margin-left: 0.625rem;
    opacity: 1;
    animation: blink 0.7s infinite;
}

.arrow-down {
    position: flex;
    cursor: pointer;
    z-index: 8;
}

.invisible-button {
    border: none;
    background: transparent;
    width: 50px;
    height: 50px;
    position: absolute;
    bottom: 0px;
    cursor: pointer;
    z-index: 8;
}

@media (max-width: 767px) {
    .brand-container {
        padding: 3rem 0.5rem 0;
    }
}

@media (min-width: 760px) {
    .brand .title {
        font-size: 1.5rem;
    }
}

@keyframes arrow-shake {
    0% {
        opacity: 1;
        transform: translateY(0);
    }

    30% {
        opacity: 0.5;
        transform: translateY(25px);
    }

    100% {
        opacity: 1;
        transform: translateY(0);
    }
}

@keyframes blink {
    0% {
        opacity: 0;
    }

    100% {
        opacity: 1;
    }
}

@keyframes titleScale {
    0% {
        opacity: 0;
        transform: scale(0.7);
    }

    100% {
        opacity: 1;
        transform: scale(1);
    }
}
</style>
