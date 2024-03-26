<template>
    <div class="error-msg">
        {{ error_msg }}
    </div>
</template>

<script>
    export default {
        props: {
            error_msg: String
        }
    }
</script>

<style scoped>
    .error-msg{
        margin: 17px 31px;
        color: red;
    }
</style>