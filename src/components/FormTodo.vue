<template>
    <div class="form-todo form-group">
        <p>
            <input placeholder="Nome" type="text" name="author" class="form-control" v-model="name">
        </p>
        <p>
            <textarea placeholder="Comentário" name="message" class="form-control" v-model="message"></textarea>
        </p>
        <button type="submit" class="btn btn-success" v-on:click="addComment">Comentar</button>
    </div>
</template>

<script>

export default {
    data() {
        return {
            'name': '',
            'message': ''
        }
    },
    methods: {
        addComment() {
            //validando se foi digitado algo
            if(this.message.trim() === '') return;

            this.$emit('add-todo', {
                name: this.name,
                message: this.message
            });

            this.name = '';
            this.message = '';
        }
    }
}

</script>