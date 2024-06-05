<template>
    <button :class="{ active: isActive }" @click="toggleActive" class="h3">
        <span v-if="showIcon" class="icon-box">
            <Icon :name="IconName" :size="IconSize"></Icon>
        </span>
        <component v-if="showText">
            {{ buttonText }}
        </component>
    </button>
</template>

<script>
export default {
    props: {
        buttonText: {
            type: String,
            default: '{{buttonText}}'
        },
        showIcon: {
            type: Boolean,
            default: false
        },
        showText: {
            type: Boolean,
            default: false
        },
        IconSize: {
            type: String,
            default: '2rem'
        },
        IconColor: {
            type: String,
            default: 'var(--100)'
        },
        IconName: {
            type: String,
            default: 'line-md:account'
        },
    },
    data() {
        return {
            isActive: false
        };
    },
    methods: {
        toggleActive() {
            this.isActive = !this.isActive;
        }
    }
};
</script>

<style scoped>
button {
    background-color: var(--700);
    color: var(--300);
    padding: 5px 5px;
    border: none;
    border-radius: 50px;
    cursor: pointer;
    transition: background-color 0.3s ease;
    font-family: Roboto;
    font-size: medium;
    border: 2px solid transparent;
}

button:hover {
    background-color: var(--primary);
}

button.active {
    background-color: transparent;
    border: 2px solid var(--100);
}
</style>