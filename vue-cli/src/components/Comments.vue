<template>
    <div class="container">
        <h1 class="mt-5">Comentários</h1>
        <hr />

        <FormTodo v-on:add-todo="addComment"></FormTodo>


        <p v-if="comments.length <= 0">Sem comentários</p>

        <div class="list-group mt-5">
            <div class="list-grou-item" v-for="(comment, index) in allComments" :key="comment.index">
                <span class="comment_author">
                    Autor: <strong>{{ comment.name }}</strong>
                </span>
                <p>{{ comment.message }}</p>

                <div>
                    <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import FormTodo from './FormTodo';

export default {
    components: {
        FormTodo
    },
    data(){
        return {
            comments:[]
        }
    },
    methods:{
        addComment(comment){
            this.comments.push(comment);
        },
        removeComment(index){
            this.comments.splice(index, 1);
        }
    },
    computed: {
        allComments(){
            return this.comments.map(comment => ({
                ...comment,
                name: comment.name.trim() === '' ? 'Anônimo' : comment.name
            }))
        }
    },
    /*watch: {
        comments(val){
            console.log('val'. val)
        }
    }*/
}

</script>
