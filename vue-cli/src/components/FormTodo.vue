<template>
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
</template>

<script>

export default {
    data(){
        return {
            name: '',
            message: ''
        }
    },
    methods:{
        addComment(){
            if(this.message.trim() === ""){
                return;
            }

            this.$emit('add-todo', {
                name: this.name,
                message: this.message,
            });

            this.name = "";
            this.message = "";
        }
    }
}

</script>
