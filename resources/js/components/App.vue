<template>
    <div class="container">
        <p>
            <router-link :to="{name: 'home'}">Главная</router-link>
            <router-link :to="{name: 'desks'}">Доски</router-link>
        </p>
        <div class="">
            <router-view></router-view>
        </div>
    </div>
</template>

<script>
export default {

}
</script>
