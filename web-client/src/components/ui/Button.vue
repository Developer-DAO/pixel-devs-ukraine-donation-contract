<script setup>
import { computed, defineProps } from 'vue'

const props = defineProps({
    color: {
        type: String,
        default: 'black',
    },
    as: {
        type: String,
        default: 'button',
    },
})

const colorClass = computed(() => {
    const colors = {
        black: 'bg-black text-white border-black dark:bg-gray-100 dark:border-gray-100 dark:text-black dark:font-medium disabled:border-0',
        indigo: 'bg-indigo-600 border border-transparent text-white hover:bg-indigo-700 disabled:opacity-60',
        blackOutline:
            'bg-white text-gray-900 border-black dark:bg-transparent dark:border-white dark:text-white disabled:opacity-60',
    }

    return colors[props.color]
})
</script>

<template>
    <component
        :is="as"
        :class="colorClass"
        class="
            inline-block
            text-center
            border
            rounded
            text-sm
            py-3
            px-4
            w-full
            disabled:bg-opacity-60
            disabled:border-opacity-60
            disabled:cursor-not-allowed
        "
    >
        <slot />
    </component>
</template>
