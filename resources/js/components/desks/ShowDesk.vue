<template>
    <div class="container mt-4">

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

        <div class="form-group">
            <input type="text"
                   id="name"
                   class="form-control"
                   name="name"
                   @blur="saveName"
                   v-model="name">
        </div>
    </div>
</template>

<script>
export default {
    props: [
        'deskId'
    ],
    data() {
        return {
            name: null,
            errored: false,
            loading: true
        };
    },
    methods: {
        saveName() {
            axios.post('/api/v1/desks/' + this.deskId, {
                _method: 'PUT',
                name: this.name
            })
                .then(response => {

                })
                .catch(error => {
                    console.log(error)
                    this.errored = true;
                })
                .finally(() => {
                    this.loading = false;
                });
        },
    },
    mounted() {
        axios.get('/api/v1/desks/' + this.deskId)
            .then(response => {
                this.name = response.data.data.name;
            })
            .catch(error => {
                console.log(error)
                this.errored = true;
            })
            .finally(() => {
                this.loading = false;
            });
    },
};
</script>
