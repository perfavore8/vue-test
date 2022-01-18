<template>
    <div class="data_row_wrapper">
        <div class="column">
            <label for="surname">Фамилия</label>
            <input class="input" type="text" v-model="modelValue.surname" name="surname" id="surname" :class="{ invalid: validationStatus.surname.$error}">
            <small for='surname' v-if="validationStatus.surname.$error">* Обязательное поле</small>
            <label for="name">Имя</label>
            <input class="input" type="text" v-model="modelValue.name" name="name" id="name" :class="{ invalid: validationStatus.name.$error}">
            <small for='name' v-if="validationStatus.name.$error">* Обязательное поле</small>          
            <labeled-input 
                id="lastname"
                name="lastname"
                label="Отчество"
            />
        </div>
        <div class="column">
            <label for="birthday">Дата рожения</label>
            <input class="input" type="date" v-model="modelValue.birthday" name="birthday" id="birthday" :class="{ invalid: validationStatus.birthday.$error}">
            <small for='birthday' v-if="validationStatus.birthday.$error">* Обязательное поле</small> 
            <label for="phone">Номер телефона</label>
            <input class="input" type="tel" v-model="modelValue.phone" name="phone" id="phone" :class="{invalid: validationStatus.phone.$error}">
            <small for='phone' v-if="validationStatus.phone.$error">*Номер должен начинаться с 7</small>    
            <small for='phone' v-if="validationStatus.phone.$error">* Обязательное поле</small>          
            <label for="gender">Пол</label>
            <div class="gender_wrapper">
                <input class="input" type='radio' v-model="modelValue.gender" name='gender' id="male" value="male"><span>М</span>
                <input class="input" type='radio' v-model="modelValue.gender" name='gender' id="female" value="female"><span>Ж</span>
            </div>
        </div>
    </div>
    <div class="data_row_wrapper">
        <div class="column">
            <label for="group">Группа клиентов</label>
            <select class="input" v-model="modelValue.group" multiple name="group" id="group" :class="{ invalid: validationStatus.group.$error}">
                <option>VIP</option>
                <option>Проблемные</option>
                <option>ОМС</option>
            </select>
            <small for='group' v-if="validationStatus.group.$error">* Обязательное поле</small> 
        </div>
        <div class="column --align-items-start">
            <label for="doc">Лечащий врач</label>
            <select class="input" name="doc" id="doc">
                <option>Иванов</option>
                <option>Захаров</option>
                <option>Чернышева</option>
            </select>
        </div>
    </div>
</template>

<script>
import LabeledInput from './InputField';
export default {
    name: 'user-info',
    props: ['modelValue', 'validationStatus'],
    emits: ['update:modelValue'],    
    components: {
        LabeledInput
    }
}
</script>

<style scoped>

template {
        width: 100%;
    }

</style>