<template>
    <div v-if="!correcr_reg">
        <div class="header">
            <div class="header-title">Регистрация</div>
            <hr/>
        </div>
        <div class="body">
            <div class="title">Заполните Ваши данные</div>
            <div class="form-container">
                <form class="name-form">
                    <input type="text" v-on:input="this.username = $event.target.value" id="name" class="form-input" placeholder="Имя">
                    <input type="email" v-on:input="this.email = $event.target.value" id="email" class="form-input" placeholder="Email">
                </form>
                <form class="post-form">
                    <select v-model="role" class="form-input" id="post-selector">
                        <option value="0" disabled selected>Должность</option>
                        <option value="1" name="value_1">Value 1</option>
                        <option value="2" name="value_2">Value 2</option>
                        <option value="3" name="value_3">Value 3</option>
                    </select>
                </form>
                <form class="pass-form">
                    <input type="password" v-on:input="this.password = $event.target.value" id="pass" class="form-input" placeholder="Пароль">
                    <input type="password" v-on:input="this.password_repeat = $event.target.value" id="repeat-pass" class="form-input" placeholder="Повторите пароль">
                </form>
            </div>
            <ErrorMsg :error_msg="this.error_msg"></ErrorMsg>
            <hr/>
        </div>
        <div class="footer">
            <div class="visibility">
                <div class="visibility-title">
                    <label class="switch">
                        <input v-on:input="this.public = $event.target.value" type="checkbox">
                        <span class="slider"></span>
                    </label>
                    Хотите чтобы Ваш профиль видели другие участники платформы?
                </div>
                <div class="visibility-desc">Включает профиль для просмотра другими пользователями по ссылке</div>
            </div>
            <div class="agreement">
                <lable class="check-mark">
                    <input v-model="agreement" type="checkbox" checked="checked">
                </lable>
                <div class="agree-desc">Регистрируясь, Вы соглашаетесь  с политикой конфиденциальности<br/> и обработкой персональных данных</div>
                <button v-on:click="checkForm()" class="reg-button">Зарегистрироваться</button>
            </div>
        </div>
    </div>
    <div v-else>
        Регистрация пройдена успешно!
    </div>
</template>

<script>
    import ErrorMsg from "./ErrorMsg.vue";
    import axios from 'axios';

    export default {
        components: {
            ErrorMsg
        },
        data() {
            return{
                agreement: true,
                public: false,
                username: "",
                role: 0,
                email: "",
                password: "",
                password_repeat: "",
                error_msg: "",
                correcr_reg: false
            }
        },
        methods: {
            checkForm() {
                if (!this.username) {
                    this.error_msg = "Введите имя пользователя";
                } else if (!this.role) {
                    this.error_msg = "Выберите должность"
                } else if (!this.email) {
                    this.error_msg = "Введите email"
                } else if (!this.password) {
                    this.error_msg = "Введите пароль"
                } else if (!this.password_repeat) {
                    this.error_msg = "Повторите пароль"
                }
                else if (this.password != this.password_repeat) {
                    this.error_msg = "Пароли не совпадают!";
                } else if(!this.agreement) {
                    this.error_msg = "Для регистрации необходимо согласиться с политикой конфиденциальности";
                } else {
                    this.error_msg = "";
                    //Не могу отправить post запрос в никуда
                    //this.sendPost();
                    this.correcr_reg = true;
                }
            },
            sendPost() {
                axios.post('/data', {
                    public: this.public,
                    username: this.username,
                    role: this.role,
                    email: this.email,
                    password: this.password,
                    password_repeat: this.password_repeat
                })
                    .then(function (response) {
                        console.log(response);
                    })
                    .catch(function (error) {
                        console.log(error);
                    });
            }
        }
    }
</script>

<style scoped>
    .error-field {
        background-color: red;
    }

    .header-title {
        font-weight: 700;
        size: 19px;
        margin: 17px 31px;
    }
    .title {
        font-weight: 500;
        size: 16px;
        margin: 17px 31px;
    }
    .form-input {
        width: 450px;
        height: 39px;
        margin: 17px 31px;
        border: 1px solid #E6E6EB;
        border-radius: 11px;
    }
    .visibility {
        margin: 17px 31px;
    }
    .visibility-title {
        font-weight: 500;
        font-size: 16px;
    }
    .visibility-desc {
        font-weight: 400;
        font-size: 14px;
        color: #696977;
        margin: 5px 44px;
    }
    #post-selector {
        color: grey;
    }

    .switch {
        position: relative;
        display: inline-block;
        width: 39px;
        height: 19px;
    }
    .switch input {
        opacity: 0;
        width: 0;
        height: 0;
    }
    .slider {
        position: absolute;
        cursor: pointer;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background-color: #ccc;
        -webkit-transition: .4s;
        transition: .4s;
        border-radius: 34px;
    }
    .slider:before {
        position: absolute;
        content: "";
        height: 19px;
        width: 19px;
        background-color: white;
        -webkit-transition: .4s;
        transition: .4s;
        border-radius: 50%;
    }
    input:checked + .slider {
        background-color: #2196F3;
    }
    input:focus + .slider {
        box-shadow: 0 0 1px #2196F3;
    }
    input:checked + .slider:before {
        -webkit-transform: translateX(20px);
        -ms-transform: translateX(20px);
        transform: translateX(20px);
    }

    .agreement {
        display: flex;
        align-items: center;
        margin: 0 31px;
    }
    .agree-desc {
        font-weight: 400;
        font-size: 14px;
        margin: 0 5px;
    }
    .reg-button {
        width: 302px;
        height: 40px;
        border-radius: 8px;
        background-color: #497ADA33;
        border: 0;
        color: #497ADA;
        font-weight: 400;
        font-size: 12px;
        cursor: pointer;
        margin: 0 84px;
        transition: all 0.5s ease;
    }
    .reg-button:hover {
        transform: scale(1.05);
    }
</style>