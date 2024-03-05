<script>
export default {
    data() {
        return {
            person: {
                lastname: '',
                firstname: '',
                middlename: '',
                email: '',
                password: ''
            },
            visibility: false,
            submitted: false
        }
    },
    methods: {
        showForm() {
            this.visibility = true
        },

        closeForm() {
            this.visibility = false
        },

        formSubmit() {
            this.person.lastname = this.lastname;
            this.person.firstname = this.firstname;
            this.person.middlename = this.middlename;
            this.person.email = this.email;
            this.person.password = this.password;
            this.submitted = true;
        }
    }
}
</script>

<template>
    <div class="start">
        <button v-show="visibility == false" class="start_button" v-on:click="showForm()">Начать</button>
        <ul v-show="submitted == true">
            <div v-for="(value, name) in this.person">
                <p>{{ name }}: {{ value }}</p>
            </div>
        </ul>
        <div v-show="visibility == true" class="overlay" v-on:click="closeForm()"></div>
        <div v-show="visibility == true" class="modal">
            <div class="title">
                <h1>Регистрация</h1>
                <span v-on:click="closeForm()">&times;</span>
            </div>
            <form id="form" v-on:submit='formSubmit()'>
                <div class="block">
                    <div class="first_col">
                        <div>
                            <label for="lastname">Фамилия</label>
                            <input type='text' v-model="person.lastname" id="lastname">
                        </div>
                        <div>
                            <label for="firstname">Имя</label>
                            <input type='text' v-model='person.firstname' id="firstname">
                        </div>
                        <div>
                            <label for="middlename">Отчество</label>
                            <input type='text' v-model="person.middlename" id="middlename">
                        </div>
                    </div>
                    <div class="second_col">
                        <div>
                            <label for="email">Email</label>
                            <input type="email" v-model="person.email" id="email">
                        </div>
                        <div>
                            <label for="password">Пароль</label>
                            <input type="password" v-model="person.password" id="password">
                        </div>
                    </div>
                </div>
                <button type="submit" class="sign_up_button">Отправить</button>
            </form>
        </div>
    </div>
</template>

<style >
button {
    padding: 15px 30px 15px 30px;
    background: gold;
    color: black;
    font-size: 24px;
    transition: all 0.25s;
    border: 0;
    border-radius: 5px;
}

button:hover {
    background: goldenrod;
    box-shadow: 0 0 7px 1px goldenrod;
    color: white;
}

.start {
    width: 100%;
    height: calc(100vh - 72px);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.modal {
    background: goldenrod;
    color: white;
    border-radius: 15px;
    min-width: 300px;
    width: 80%;
    max-width: 500px;
    text-align: center;
    padding: 20px 30px 20px 30px;
    z-index: 1;
}

.overlay {
    position: fixed;
    width: 100%;
    height: calc(100vh - 72px);
    background: black;
    opacity: 40%;
    z-index: 0;
}

.title {
    display: flex;
    justify-content: space-between;

}

.modal h1 {
    margin-bottom: 20px;
    margin-left: 30%;
}

span {
    font-size: 24px;
}

span:hover {
    cursor: pointer;
}

.block {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    flex-direction: row;
    gap: 30px;
    font-size: 20px;
    margin-bottom: 20px;
}

.first_col,
.second_col {
    display: flex;
    min-width: 47%;
    width: 47%;
    flex-wrap: wrap;
    flex-direction: column;
    gap: 10px;
}

.first_col div,
.second_col div {
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    justify-content: space-evenly;
    text-align: left;
    gap: 10px;
}

.first_col input,
.second_col input {
    background: transparent;
    border: 0;
    padding: 0 0 4px 0;
    border-bottom: 1px solid white;
    outline: 0;
    color: white;
    transition: all 0.25s;
}

.sign_up_button {
    font-size: 20px;
    background: goldenrod;
    color: white;
    border: 3px solid white;
}

.sign_up_button:hover {
    background: white;
    color: goldenrod;
    box-shadow: 0;
}

@media (max-width: 625px) {

    .first_col,
    .second_col {
        width: 100%;
    }
}
</style>
