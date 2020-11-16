<template>
     <div class="card">
                <div class="card-header">En que estas pensando</div>

                <div class="card-body">

                    <form action=""
                    v-on:submit.prevent="newThought()"
                    >
                        <div class="form-group">
                            <label for="thought">Ahora estoy pensando en: </label>
                            <input type="text" class="form-control" name='thought'
                            v-model="description"
                            >
                            <hr/>
                            <button type="submit" class="btn btn-primary">
                                Enviar Pensamiento
                            </button>
                        </div>
                    </form>

                </div>
            </div>

</template>

<script>
    export default {
        data(){
            return {
                description: ''
            }
        },
        mounted() {
            console.log('Component mounted.')
        },
        methods:{
            newThought(){
                //alert(this.description);
                let thought={
                    id:4,
                    description: this.description,
                    created_at: '11/22/3333'
                };
                this.$emit('new', thought);
                this.description ='';

            }
        }
    }
</script>
