<template>
    <svg class="spinner" :width="width" :height="height" viewBox="0 0 50 50">
        <circle class="path" cx="25" cy="25" r="20" fill="none" :stroke="color" :stroke-width="widthStroke"></circle>
    </svg>
</template>

<script>
export default {
    props: {
        width: Number,
        height: Number,
        color: {type: String, default: "white"},
        widthStroke: {
            type: Number,
            default: 8
        }
    }
}
</script>
<style>
    .spinner {
        animation: rotate 2s linear infinite;
    }
    .spinner .path {
        stroke-linecap: round;
        animation: dash 1.5s ease-in-out infinite;
    }
    @keyframes rotate {
        100% {
            transform: rotate(360deg);
        }
    }
    @keyframes dash {
        0% {
            stroke-dasharray: 1, 150;
            stroke-dashoffset: 0;
        }
        50% {
            stroke-dasharray: 90, 150;
            stroke-dashoffset: -35;
        }
        100% {
            stroke-dasharray: 90, 150;
            stroke-dashoffset: -124;
        }
    }
</style>