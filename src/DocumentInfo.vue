<template>
<div class="data_row_wrapper">
    <div class="column">
        <label for="type">Тип документа</label>
            <select class="input" v-model="modelValue.type" name="type" id="type" :class="{ invalid: validationStatus.type.$error}">
                <option>Паспорт</option>
                <option>Вод. удостоверение</option>
                <option>Вод. удостоверение</option>
            </select>
            <small for='type' v-if="validationStatus.type.$error">* Обязательное поле</small>
        <labeled-input 
            id="series"
            name="series"
            label="Серия"
        />
        <labeled-input 
            id="number"
            name="number"
            label="Номер"
        />
    </div>
    <div class="column">
        <labeled-input 
            id="issued"
            name="issued"
            label="Кем выдан"
        />
        <label for="dateIssue">Дата выдачи</label>
        <input class="input" type="date" v-model="modelValue.dateIssue" name="dateIssue" id="dateIssue" :class="{ invalid: validationStatus.dateIssue.$error}">
        <small for='dateIssue' v-if="validationStatus.dateIssue.$error">* Обязательное поле</small> 
    </div>
</div>
</template>

<script>
import LabeledInput from './InputField.vue';

export default {
    name: 'document-info',
    emits: ['update:modelValue'],
    props: ['modelValue', 'validationStatus'],
    components: {
        LabeledInput
    },
}
</script>

<style>

</style>