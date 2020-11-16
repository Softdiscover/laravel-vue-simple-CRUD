<template>
<div class="row justify-content-center">
        <div class="col-md-8">
            <form-component @new="addThought"></form-component>
            <hr/>

            <thought-component
            v-for="(thought, index) in thoughts"
            :key='thought.id'
            :thought='thought'
            @update="updateThought(index, ...arguments)"
            @delete="deleteThought(index)"
            ></thought-component>

        </div>
    </div>
</template>

<script>
    export default {

        data(){
            return {
                thoughts: [
                {
                    'id':1,
                    'description':'lorem ipsum  asdlfj alsdkfj alsdjf laksjdf lasjd flkajsd fljkas dlfj',
                    'created_at':'17/07/2018'
                },
                {
                    'id':2,
                    'description':'lorem ipsum2  asdlfj alsdkfj alsdjf laksjdf lasjd flkajsd fljkas dlfj',
                    'created_at':'17/07/2020'
                }

                ]
            }
        },

        mounted() {
            console.log('Component mounted.')

        },
        methods: {
            addThought(thought){
                this.thoughts.push(thought);
            },
            deleteThought(index){

                this.thoughts.splice(index,1)
            },
             updateThought(index, thought){

                this.thoughts[index] = thought;
            }
        }


    }
</script>
