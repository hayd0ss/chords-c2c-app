<template>
    <div class="profile-div">
        <div :style="{ 'background' : bg, 'border' : 'none' }" class="user-image">
            <h1>{{ username.slice(0,1) }}</h1>
        </div>
        <div class="user-details">
            <p class="username">{{ username }}</p>
            <p>{{ userEmail }}</p>
        </div>
        <input type="button" class="button edit-profile-button" value="EDIT PROFILE">
    </div>
</template>

<script>
import ProductService from '../services/ProductService.js';

export default {
    data() {
        return {
            record: null,
            bg: "",
            username: "Bindy",
            userEmail: "user@gmail.com"
        }
    },
    methods: {
        capitalise() {
            return this.username = this.username.charAt(0).toUpperCase() + this.username.slice(1)
        },
        generate() {
            var username = this.username.toLowerCase()
            username = username.slice(0,1)
            var hexCode1
            var hexCode2
            if (username == "c" || username == "d" || username == "e" || username == "p" || username == "q") {
                hexCode1 = "6ed7ff"
                hexCode2 = "ff00c6"
            } else if (username == "f" || username == "g" || username == "h" || username == "i" || username == "j" || username == "r" || username == "s") {
                hexCode1 = "ff7ffc"
                hexCode2 = "8100b8"
            } else if (username == "k" || username == "l" || username == "m" || username == "n" || username == "o" || username == "t" || username == "u") {
                hexCode1 = "ff0000"
                hexCode2 = "ffe291"
            } else if (username == "a" || username == "b" || username == "v" || username == "w" || username == "x" || username == "y" || username == "z") {
                hexCode1 = "e0ff00"
                hexCode2 = "00ff2a"
            }
             else (hexCode1 = "00ffe2", hexCode2 = "9199ff")

            var gradient = "linear-gradient(0deg, #" + hexCode1 + ", " + "#" + hexCode2 + ")";

            this.bg = gradient
        }
    },
    created() {
        ProductService.getData(this.id)
            .then(response => {
                this.record = response.data
            })
            .catch(error => {
                console.log(error);
            })
    },
    beforeMount() {
        this.generate()
        this.capitalise()
    }
}

</script>

<style lang="scss" scoped>
.profile-div {
    margin-top: 3rem;
    border: solid 1px grey;
    padding: 1rem;
    width: 18rem;
    height: 22rem;
    padding-bottom: 2rem;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;

    p {
        margin-bottom: 0.6rem;
    }
}

.username {
    font-weight: 800;
    font-size: 1.1rem;
}

.edit-profile-button {
    min-width: 10rem;
    margin: 2rem 0rem;
    font-size: 0.8rem;
}

.user-image {
    margin: 0 auto;
    min-width: 10rem;
    min-height: 10rem;
    border-radius: 50%;
    background-color: white;
    border: 1px solid grey;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;
    transform: translateY(-25%);

    h1 {
        font-size: 4em;
        color: white;
    }
}
</style>