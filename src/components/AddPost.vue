<template>
 <form @submit.prevent="createPost" :class="{ error: maxCharacters > 20 }">
            <label for="title">A bejegyzés címe:</label>
            <input v-model="userTitleInput" type="text" placeholder="írja ide a szöveget" id="title"/>
            <label for="text">Fő szöveg:<span>{{ maxCharacters }} / 20</span>
            </label>
            <textarea v-model="userTextInput" 
            id="text" 
            placeholder="írja ide a szöveget"
            ></textarea>
            <button>Hozzáadás</button>        
        </form>
</template>

<script>
export default {
    name: 'Articles',
    data() {
        return{
            userTitleInput: "",
            userTextInput: "",
        };
    },
    methods: {
    createPost() {
        if (this.maxCharacters > 20) {
            return; 
        }

        if(this.userTitleInput !== "" && this.userTextInput !=="") {
            this.$emit('add-post', this.userTitleInput, this.userTextInput)

        this.userTitleInput = "";
        this.userTextInput = "";
        }
    },
},
computed: {
    maxCharacters() {
        return this.userTextInput.length;
    },
  },
};
</script>

<style scoped>
    aside {
    margin-top: 20px;    
}

form.error label {
    color:rgb(210, 31, 31);
}

form label {
    color: #505050;
}

form input,
form textarea {
    width: 100%;
    background: #c6c391;
    border-radius: 5px;
    border: 2px solid #5e5b21;
    padding: 8px 10px;
    font-size: 14px;
    color: #5e5b21;
    outline: none;
    margin-bottom: 10px;
    resize: none;
}
aside form button {
    float: right;
    background: #aaa771;
    border: 2px solid #5e5b21;
    border-bottom-width: 4px;
    padding: 10px 12px;
    font-size: 13px;
    font-weight: bold;
    color: #5e5b21;
    border-radius: 5px;
    cursor: pointer;
    transition: all 500ms ease;
}

aside form button:hover {
    margin-top: 2px;
    border-bottom-width: 2px;
}


</style>