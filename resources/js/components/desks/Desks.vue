<template>
    <div class="container">
        <h2>Доски</h2>

        <div class="alert alert-danger"
             role="alert"
             v-if="errored">
            Ошибка загрузки данных!
        </div>

        <div class="spinner-border"
             style="width: 3rem; height: 3rem"
             role="status"
             v-if="loading">
            <span class="sr-only">Loading...</span>
        </div>

        <div class="row">
            <div class="col-lg-4"
                 v-for="desk in desks">
                <div class="card mt-3">
                    <a class="card-body"
                       href="#">
                        <h5 class="card-title">{{ desk.name }}</h5>
                    </a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            desks: [],
            errored: false,
            loading: true
        };
    },
    mounted() {
        axios.get('/api/v1/desks')
        .then(response => {
            this.desks = response.data.data;
        })
        .catch(error => {
            console.log(error)
            this.errored = true;
        })
        .finally(() => {
            this.loading = false;
        })
    }
};
</script>
