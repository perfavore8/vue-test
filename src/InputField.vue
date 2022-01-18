<template>
    <label for="{{id}}">{{ label }}</label>
    <input 
        class="input"
        type="text"
        @input="handleInput"
        :name="name"
        :id="id"
    >
</template>

<script>
export default {
    name: 'labeled-input',
    emits: ['update:modelValue'],
    props: ['name', 'id', 'modelValue', 'label'],

    methods: {
        handleInput(e) {
            this.$emit(`update:modelValue`, e.target.value)
        }
    }
}
</script>

<style scoped>
    template {
        width: 100%;
    }

    input {
        /* border-color: rgba(21, 194, 156, 0.781); */
        border-radius: 5px;
        border-width: 2px;
    }

    .invalid {
        border-color: rgba(219, 42, 42, 0.781);
        border-radius: 5px;
        border-width: 2px;
    }
</style>