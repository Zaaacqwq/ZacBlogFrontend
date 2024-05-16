<template>
    <svg aria-hidden="true" class="svg-icon" :width="size" :height="size">
        <use :xlink:href="symbolId" :fill="color" />
    </svg>
</template>


<script>
export default {
    props: {
        prefix: {
            type: String,
            default: 'icon'
        },
        iconClass: {
            type: String,
            required: false
        },
        color: {
            type: String
        },
        size: {
            type: String,
            default: '1rem'
        }
    },
    computed: {
        symbolId() {
            return `#${this.prefix}-${this.iconClass}`;
        }
    }
}
</script>


<style scoped>
.svg-icon {
    vertical-align: -0.15em;
    overflow: hidden;
    fill: currentColor;
}
</style>
