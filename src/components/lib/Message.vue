<template>
    <article class="message" :class="[type, { 'is-medium': prominent, 'shadow': shadow }]">
        <div class="message-header" v-if="hasHeader">
            <slot name="message-header"></slot>
            <button class="delete"
                    aria-label="delete"
                    v-if="dismissiable"
                    @click.prevent="closeMessage">
            </button>
        </div>
        <div class="message-body">
            <slot name="message-body"></slot>
        </div>
        <footer class="message-footer" :class="[{'align-right': footerRight}]" v-if="hasFooter">
            <slot name="message-footer"></slot>
        </footer>
    </article>
</template>
<script>
import { colors } from './utils.js';
export default {
    name: 'Message',
    props: {
        type: {
            type: String,
            validator: function(value) {
                return colors().includes(value);
            }
        },
        dismissiable: {
            type: Boolean,
            default: true
        },
        prominent: {
            type: Boolean,
            default: false
        },
        shadow: {
            type: Boolean,
            default: false
        },
        show: {
            type: Boolean,
            default: false
        },
        timeout: {
            type: Number,
            default: 0
        },
        hasFooter: {
            type: Boolean,
            default: false
        },
        footerRight: {
            type: Boolean,
            default: true
        },
        hasHeader: {
            type: Boolean,
            default: true
        },
        modelValue: {
            type: Boolean,
            default: true
        }
    },
    methods: {
        closeMessage() {
            this.$emit('update:modelValue', false);
        }
    },
    emits: {
        'update:modelValue': null
    },
    mounted() {
        if(this.timeout !== 0) {
            // Convert to second first.
            let timeout = this.timeout * 1000;
            setTimeout(() => {
                this.closeMessage();
            }, timeout);
        }
    }
}
</script>
<style lang="scss">
.message-footer {
    padding: $message-body-padding;
    padding-top: 0;
}
.message-footer.align-right {
    @media (min-width: $break-small) {
        display: flex;
        justify-content: flex-end;
    }
}
</style>