<template>
    <div class="container">
        <h1 class="mt-5">Comentários</h1>
        <hr />

        <div class="form-todo form-group">
            <div class="row mb-1">
                <input placeholder="nome" type="text" name="author" class="form-control" v-model="name" />
            </div>
            <div class="row mb-1">
                <textarea placeholder="Comentário" name="message" class="form-control" v-model="message"></textarea>
            </div>

            <div class="row mb-1">
                <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
            </div>

        </div>

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

export default {
    data(){
        return {
            comments:[],
            name: '',
            message: ''
        }
    },
    methods:{
        addComment(){
            if(this.message.trim() === ""){
                return;
            }

            this.comments.push({
                name: this.name,
                message: this.message
            });

            this.name = "";
            this.message = "";
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
