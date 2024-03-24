<template>
    <div>
        <div class="header">Регистрация</div>
        <div class="body">
            <div class="title"></div>
            <form>
                <input type="text" id="name" placeholder="Имя">
                <input type="email" id="email" placeholder="Email">
                <select>
                    <option value="value_1">Value 1</option>
                    <option value="value_2">Value 2</option>
                    <option value="value_3">Value 3</option>
                </select>
                <input type="password" id="pass" placeholder="Пароль">
                <input type="password" id="repeat-pass" placeholder="Повторите пароль">
            </form>
        </div>
        <div class="footer">
            <div class="visibility">
                <div id="selector"></div>
                <div class="visibility-title">Хотите чтобы Ваш профиль видели другие участники платформы? </div>
                <div class="visibility-desc">Включает профиль для просмотра другими пользователями по ссылке</div>
            </div>
            <div class="agreement">
                <div class="check-mark"></div>
                <div class="agree-desc">Регистрируясь, Вы соглашаетесь  с политикой конфиденциальности и обработкой персональных данных</div>
            </div>
            <button>Зарегистрироваться</button>
        </div>
    </div>
</template>

<script>
    export default {

    }
</script>

<style scoped>

</style>