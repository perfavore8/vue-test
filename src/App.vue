<template>
    <div>
        <label for="surname">Фамилия</label>
        <input type="text" name="surname" id="surname">
        <label for="name">Имя</label>
        <input type="text" name="name" id="name">
        <label for="lastname">Отчество</label>
        <input type="text" name="lastname" id="lastname">
        <label for="birthday">Дата родов</label>
        <input type="date" name="birthday" id="birthday">
        <label for="phone">Номер телефона</label>
        <input type="tel" name="phone" id="phone">
        <label for="gender">Пол</label>
        <input type='radio' name='gender' id="male" value="male"><span>Male</span>
        <input type='radio' name='gender' id="female" value="female"><span>Female</span>
        <label for="group">Группа клиентов</label>
        <select multiple name="group" id="group">
            <option>Grumpy</option>
            <option>Happy</option>
            <option>Sleepy</option>
            <option>Bashful</option>
            <option>Sneezy</option>
            <option>Dopey</option>
            <option>Doc</option>
        </select>
        <label for="doc">Лечащий врач</label>
        <select name="doc" id="doc">
            <option>Иванов</option>
            <option>Захаров</option>
            <option>Чернышева</option>
        </select>
        <label for="sms">Не отправлять СМС</label>
        <input type="checkbox" name="sms" id="sms" checked>
    </div>
</template>

<script>
export default {
    data() {
        return { 
            likes:0,
            dislikes:0,
        }
    },

    methods: {
        addLike() {
            this.likes += 1;
        },
        addDislike() {
            this.dislikes += 1;
        }
    }
}

</script>

<style>

</style>