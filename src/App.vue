<template>
    <div class='row' @submit.prevent="onSubmit">
        <user-info v-model="state.user" :validationStatus="v$.state.user" />
        <address-info v-model="state.address" :validationStatus="v$.state.address" />
        <document-info v-model="state.document" :validationStatus="v$.state.document" />
        <label for="sms">Не отправлять СМС</label>
        <input v-model="sms" type="checkbox" name="sms" id="sms">
        <button type="submit" @click="onSubmit">Отправить</button>
    </div>
</template>

<script type="text/javascript">
import LabeledInput from './InputField.vue';
import AddressInfo from './AddressInfo.vue';
import DocumentInfo from './DocumentInfo.vue';
import {required, numeric} from '@vuelidate/validators';
import UserInfo from './UserInfo.vue';
import useVuelidate from '@vuelidate/core';

export default {
    components: {
        LabeledInput,
        UserInfo,
        AddressInfo,
        DocumentInfo
    },

    setup() {
        return { v$: useVuelidate() }
    },

    data() {
        return {
            state: {
                user: { 
                    surname: null,
                    name: null,
                    lastname: null,
                    birthday: undefined,
                    phone: null,
                    gender: 'female',
                    group: '',
                    doc: '',
                    sms: true,
                },
                address: {
                    index: null,
                    country: null,
                    region: null,
                    city: null,
                    street: null,
                    house: null
                },
                document: {
                    type: '',
                    series: null,
                    number: null,
                    issued: null,
                    dateIssue: null,
                }
            }
        }
    },

    validations() {
        return {
            state: {
                user: {
                    surname: {required},
                    name: {required},
                    birthday: {required},
                    phone: {required, numeric},
                    group: {required},
                },
                address: {
                    city: { required },
                },
                document: {
                    type: { required },
                    dateIssue: { required },
                }
            }
        }
    },

    methods: {
        onSubmit() {
            this.v$.$validate()
            console.table(this.state.user)
            console.table(this.state.address)            
        }
    }
}

</script>

<style>

html, body {
    width: 100vw;
    min-height: 100vh;
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
    width: 90vw;
    max-width: 600px;
}

.input {
    width: inherit;
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
    border: 1px solid black;
    border-radius: 5px;
    padding: 15px 10px;
    box-shadow: 10px 8px rgba(0,0,0, .15);
}

.column { 
    min-width:30%;
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: space-around;
    /* justify-content: space-around; */
    gap: 5px;
    padding-right: 7px;
}

.column > .input {
    min-width: 100%;
}

.--align-items-start {
    align-items: start;
    justify-content: start;
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