<template> 
    <div v-if='articles.length > 0'id="articles">
        <div class="post" v-for="el in articles" :key="el.id">
            <button @click="deletePost(el.id)">Törlés</button>
            <h2>{{ el.title }}</h2>
            <p>{{ el.text }}</p>
        </div>
    </div>
    <h1 class="empty" v-else>Jelenleg nincsenek cikkek!</h1>
</template>

<script>
    export default {
        name: 'Articles',
        data() {
            return{
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
            }
        }
    };
</script>

<style scoped>
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

#articles .post button {
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

#articles .post button:hover {
    margin-top: 2px;
    border-bottom-width: 2px;
}

.empty {
    margin: 20px;
    color:#502B7B
}

</style>