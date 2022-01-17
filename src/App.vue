<template>
    <div class='row' @submit.prevent="onSubmit">
        <div class="data_row_wrapper">
            <div class="column">
                <labeled-input 
                    id="surname"
                    name="surname"
                    v-model="surname"
                    :valid="v$.surname"
                    label="Фамилия"
                />
                <labeled-input 
                    id="name"
                    name="name"
                    v-model="name"
                    :valid="v$.name"
                    label="Имя"
                />
                <labeled-input 
                    id="lastname"
                    name="lastname"
                    v-model="lastname"
                    :valid="v$.lastname"
                    label="Отчество"
                />
            </div>
            <div class="column">
                <label for="birthday">Дата рожения</label>
                <input class="input" type="date" v-model="birthday" name="birthday" id="birthday" :class="{ invalid: v$.birthday.$error}">
                <label for="phone">Номер телефона</label>
                <input class="input" type="tel" v-model="phone" name="phone" id="phone" :class="{invalid: (v$.phone.$error) || (!v$.phone.numeric)}">
                <label for="gender">Пол</label>
                <div class="gender_wrapper">
                    <input class="input" type='radio' v-model="gender" name='gender' id="male" value="male"><span>Мужской</span>
                    <input class="input" type='radio' v-model="gender" name='gender' id="female" value="female"><span>Женский</span>
                </div>
            </div>
        </div>
        <div class="data_row_wrapper">
            <div class="column">
                <label for="group">Группа клиентов</label>
                <select class="input" v-model="group" multiple name="group" id="group" :class="{ invalid: v$.group.$error}">
                    <option>VIP</option>
                    <option>Проблемные</option>
                    <option>ОМС</option>
                </select>
            </div>
            <div class="column --align-items-center">
                <label for="doc">Лечащий врач</label>
                <select class="input" v-model="doc" name="doc" id="doc" :class="{ invalid: v$.doc.$error}">
                    <option>Иванов</option>
                    <option>Захаров</option>
                    <option>Чернышева</option>
                </select>
            </div>
        </div>
        <label for="sms">Не отправлять СМС</label>
        <input v-model="sms" type="checkbox" name="sms" id="sms">

        <button type="submit" @click="onSubmit">Отправить</button>
    </div>
</template>

<script type="text/javascript">
import useVuelidate from '@vuelidate/core'
import {required, numeric} from '@vuelidate/validators';
import LabeledInput from './InputField.vue';

export default {
    setup() {
        return { v$: useVuelidate() }
    },
    components: {
        LabeledInput
    },
    data() {
        return { 
            surname: null,
            name: null,
            lastname: null,
            birthday: undefined,
            phone: null,
            gender: 'female',
            group: '',
            doc: '',
            sms: true,
        }
    },

    validations() {
        return {
        surname: {required},
        name: {required},
        lastname: {required},
        birthday: {required},
        phone: {required, numeric},
        group: {required},
        doc: {required},

}
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
            if (this.v$.$invalid) {
                this.v$.$touch()
                return
            } else {
                this.commit()
            }
        }
    }
}

</script>

<style>

html, body {
    width: 100vw;
    height: 100vh;
    margin: 0;
    padding: 0;
}

body {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.row {
    width: 40vw;
}

.input {
    /* border-color: rgba(21, 194, 156, 0.781);  */
    border-radius: 5px;
    border-width: 2px;
}

.invalid {
    border-color: rgba(219, 42, 42, 0.781);
    border-radius: 5px;
    border-width: 2px;
}

.data_row_wrapper {
    width: 100%;
    display: flex;
    flex-direction: row;
    align-items: space-around;
    justify-content: space-around;
    gap: 20px;
    margin-bottom: 10px;
}

.column { 
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: space-around;
    justify-content: space-around;
    gap: 5px;
}

.column > .input {
    width: 100%;
}

.--align-items-center {
    align-items: flex-start;
    justify-content: center;
}

.row {
    margin: 0 auto;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    margin: auto;
}

.gender_wrapper {
    display: flex;
    flex-direction: row;
}
</style>