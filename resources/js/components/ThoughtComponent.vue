<template>

     <div class="card mt-2">
                <div class="card-header">'Publicado en {{ thought.created_at}} - update at : {{ thought.updated_at}}</div>

                <div class="card-body">

                    <input v-if="editMode" type="text" class="form-control" name="" id="" v-model="thought.description">
                    <p v-else>
                    {{thought.description}}
                    </p>

                </div>
                <div class="card-footer">


                    <button v-if="editMode" class="btn btn-primary" v-on:click="onClickUpdate()" >
                        Guardar Cambios
                    </button>
                    <button v-else class="btn btn-primary" v-on:click="onClickEdit()" >
                        Editar
                    </button>

                    <button class="btn btn-danger"
                    v-on:click="onClickDelete()"
                    >
                        Eliminar
                    </button>
                </div>
            </div>

</template>

<script>
    export default {
        props: ['thought'],
        data(){
            return {
                editMode: false
            }
        },
        mounted() {
            console.log('Component mounted.')
        },
        methods:{
            onClickDelete(){
                this.$emit('delete');
                axios.delete(`/thoughts/${this.thought.id}`).then(
               () =>{
                     this.$emit('delete');
                }

                );

            },
            onClickEdit(){
                this.editMode = true;
                this.$emit('edit');
            },
            onClickUpdate(){

const params ={
    description: this.thought.description
};

            axios.put(`/thoughts/${this.thought.id}`, params).then(
                (response)=>{
                   this.editMode = false;
                   const thought = response.data;
                this.$emit('update',this.thought);
                }
            );


            }
        }
    }
</script>
