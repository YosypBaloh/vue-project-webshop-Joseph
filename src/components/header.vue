<template>
    <div class="header">
        <span class="logo">{{ title }}</span>
        
        <span class="right-side">
            <span class="user">{{ fullName }} ({{ user.rating }})</span>
            <button @click="addRating">+</button>
        </span>
    </div>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            user: {
                name: 'Timcsi',
                surname: 'Balog',
                age:'20',
                rating: 0,
                email: 'john@doe.com',
            },
            allRating: 0
        };
    },
    computed: {
        fullName(){
            return `Szia, ${this.user.name} ${this.user.surname}`;
        },
    },
    methods:{
        addRating(){
            this.user.rating++;
            this.allRating++;
        }
    },
    mounted() {
      this.addRating();
    },

    watch: {
      allRating(newValue, oldValue) {
        if (newValue > 5) console.log(`${newValue} - ${oldValue}`);
      },
    },

    props: {
        title: {
            type: String,
            required: true,
        },
    },
};
</script>

<style lang='css' scoped>
.header {
    background: #333;
    color:#fff;
    padding: 20px;
    border-bottom: 2px solid #000;
    
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.header .logo {
    font-size: 20px;
}

.header .right-side {
    display: flex;
    align-items: center;
    gap: 7px;
}

.header button {
    border: 0;
    background: lightgray;
    border-radius: 7px;
    padding: 5px 7px;
    font-size: 14px;
    font-weight: bold;
    cursor: pointer;
}

.header button:hover {
    background: #000;
    color: #fafafa;
}
</style>