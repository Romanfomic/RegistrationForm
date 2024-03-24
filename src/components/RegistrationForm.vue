<template>
    <div>
        <div class="header">
            <div class="header-title">Регистрация</div>
            <hr/>
        </div>
        <div class="body">
            <div class="title">Заполните Ваши данные</div>
            <div class="form-container">
                <form class="name-form">
                    <input type="text" id="name" class="form-input" placeholder="Имя">
                    <input type="email" id="email" class="form-input" placeholder="Email">
                </form>
                <form class="post-form">
                    <select class="form-input" id="post-selector">
                        <option disabled selected>Должность</option>
                        <option value="value_1">Value 1</option>
                        <option value="value_2">Value 2</option>
                        <option value="value_3">Value 3</option>
                    </select>
                </form>
                <form class="pass-form">
                    <input type="password" id="pass" class="form-input" placeholder="Пароль">
                    <input type="password" id="repeat-pass" class="form-input" placeholder="Повторите пароль">
                </form>
            </div>
            <hr/>
        </div>
        <div class="footer">
            <div class="visibility">
                <div class="visibility-title">
                    <label class="switch">
                        <input type="checkbox">
                        <span class="slider"></span>
                    </label>
                    Хотите чтобы Ваш профиль видели другие участники платформы?
                </div>
                <div class="visibility-desc">Включает профиль для просмотра другими пользователями по ссылке</div>
            </div>
            <div class="agreement">
                <lable class="check-mark">
                    <input type="checkbox">
                </lable>
                <div class="agree-desc">Регистрируясь, Вы соглашаетесь  с политикой конфиденциальности<br/> и обработкой персональных данных</div>
                <button class="reg-button">Зарегистрироваться</button>
            </div>
        </div>
    </div>
</template>

<script>
    export default {

    }
</script>

<style scoped>

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