<template> 
    <main>
        <div v-if='articles.length > 0'id="articles">
            <div class="post" v-for="el in articles" :key="el.id">
                <button @click="deletePost(el.id)">Törlés</button>
                <h2>{{ el.title }}</h2>
                <p>{{ el.text }}</p>
            </div>
        </div>
        <h1 class="empty" v-else>Jelenleg nincsenek cikkek!</h1>
    </main>
    <aside>
        <form @submit.prevent="createPost" :class="{ error: maxCharacters > 20 }">
            <label for="title">A bejegyzés címe:</label>
            <input v-model="userTitleInput" type="text" placeholder="írja ide a szöveget" id="title"/>
            <label for="text">Fő szöveg:<span>{{ maxCharacters }} / 20</span>
            </label>
            <textarea v-model="userTextInput" id="text" placeholder="írja ide a szöveget"></textarea>
            <button>Hozzáadás</button>        
        </form>
    </aside>
</template>

<script>
export default {
    name: 'Articles',
    data() {
        return{
            userTitleInput: "",
            userTextInput: "",
        articles: [
            {
                id: 1,
                title: "Az Ókori Egyiptomi Viselet: Funkció és Rituálé",
                text: "A lenvászon könnyed használata és a geometrikus formák dominanciája az ókori viseletben, különös tekintettel a 'schenti' szoknyára és a 'kalasiris' ruhára.",
            },
            {
                id: 2,
                title: "A Reneszánsz Korszak: Díszítés és Rétegek",
                text: "A gazdag brokátok, a szűk fűzők és a puffos ujjú ruhák megjelenése, ami a társadalmi státusz és a vagyon hangsúlyozására szolgált.",
            },
            {
                id: 3,
                title: "A 19. századi Krinolin: Térfogat és Elegancia",
                text: "A krinolin (abroncsos alsószoknya) elterjedése, mint a női sziluett drámai megnövelésének eszköze, és a korabeli divat társadalmi korlátai.",
            },
            {
                id: 4,
                title: "Coco Chanel és a Kis Fekete Ruha Forradalma",
                text: "A 20. századi modernizmus belépése a divatba: a praktikus, elegáns és időtlen 'Little Black Dress' születése, amely felszabadította a nőket a szűk fűzők alól.",
            },
            ],
        };
    },
    methods: {
        deletePost(id) {
            this.articles = this.articles.filter((el) => el.id !== id)
        },
    createPost() {
        if(this.userTitleInput !== "" && this.userTextInput !=="") {
            this.articles.unshift({
                id: Math.random() * 1000,
                title: this.userTitleInput,
            text: this.userTextInput,
        });

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
main {
float: left;
width: 60%;
}

aside {
    float: left;
    width: 20%;
    margin-left: 10%;
}

#articles {
    margin:20px;
}

#articles .post {
    background: #c6c391;
    padding: 20px;
    margin-bottom: 20px;
    border: 1px solid #aaa771;
    color: #5e5b21;
    float:left;
    width: 100%;
}

#articles .post button,
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

#articles .post button:hover,
aside form button:hover {
    margin-top: 2px;
    border-bottom-width: 2px;
}

.empty {
    margin: 20px;
    color:#5e5b21
}

aside {
    margin-top: 20px;    
}

aside form.error label {
    color:rgb(210, 31, 31);
}

aside form label {
    color: #505050;
}

aside form input,
aside form textarea {
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

</style>