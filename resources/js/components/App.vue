<template>
    <div>
        <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
            <div class="container">
                <div class="navbar-nav">
                    <router-link class="nav-item nav-link" :to="{name: 'home'}">Главная</router-link>
                    <router-link class="nav-item nav-link" :to="{name: 'desks'}">Доски</router-link>
                </div>
            </div>
        </nav>
        <div class="container">
            <div class="">
                <router-view></router-view>
            </div>
        </div>
    </div>
</template>

<script>
export default {

}
</script>
