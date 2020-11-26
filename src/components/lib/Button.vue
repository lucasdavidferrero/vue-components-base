<template>
    <button class="button" :class="[{'is-loading': loading}]">
        <span class="icon" v-if="icon">
            <i :class="[icon]"></i>
        </span>
        <span>
            <slot>Button</slot>
        </span>
    </button>
</template>
<script>

export default {
    name: 'Button',
    props: {
        loading: {
            type: Boolean,
            default: false
        },
        icon: {
            type: String,
            default: null
        }
    },
    emits: {
        
    }
}
</script>
