<template>
    <div @submit.prevent="onSubmit">
        <label for="surname">Фамилия</label>
        <input type="text" v-model="surname" name="surname" id="surname" :class="{invalid: ($v.surname.$dirty && !$v.surname.required)}">
        <label for="name">Имя</label>
        <input type="text" v-model="name" name="name" id="name">
        <label for="lastname">Отчество</label>
        <input type="text" v-model="lastname" name="lastname" id="lastname">
        <label for="birthday">Дата рожения</label>
        <input type="date" v-model="birthday" name="birthday" id="birthday">
        <label for="phone">Номер телефона</label>
        <input type="tel" v-model="phone" name="phone" id="phone">
        <label for="gender">Пол</label>
        <input type='radio' v-model="gender" name='gender' id="male" value="male"><span>Мужской</span>
        <input type='radio' v-model="gender" name='gender' id="female" value="female"><span>Женский</span>
        <label for="group">Группа клиентов</label>
        <select v-model="group" multiple name="group" id="group">
            <option>VIP</option>
            <option>Проблемные</option>
            <option>ОМС</option>
        </select>
        <label for="doc">Лечащий врач</label>
        <select v-model="doc" name="doc" id="doc">
            <option>Иванов</option>
            <option>Захаров</option>
            <option>Чернышева</option>
        </select>
        <label for="sms">Не отправлять СМС</label>
        <input v-model="sms" type="checkbox" name="sms" id="sms" checked>

        <button @click="commit">Отправить</button>
    </div>
</template>

<script type="text/javascript">
import Vue from 'vue'
import {required, numeric} from '@vuelidate/validators'

export default {
    data() {
        return { 
            surname: null,
            name: null,
            lastname: null,
            birthday: undefined,
            phone: null,
            gender: null,
            group: '',
            doc: '',
            sms: null,
        }
    },

    validations: {
        surname: {required},
        name: {required},
        lastname: {required},
        birthday: {required},
        phone: {required, numeric},
        gender: {required},
        group: {required},
        doc: {required},

    },

    methods: {
        commit() {
            console.log(this.surname);
            console.log(this.name);
            console.log(this.lastname);
            console.log(this.birthday);
            console.log(this.phone);
            console.log(this.gender);
            console.log(this.group);
            console.log(this.doc);
            console.log(this.sms);
        },
        onSubmit() {
            if (this.$v.$invalid) {
                this.$v.$touch()
                return
            }
        }
    }
}

</script>

<style>

</style>