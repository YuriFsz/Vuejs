<script>
import axios from "https://cdn.skypack.dev/axios@0.27.2";

export default {
    data() {
        return {
            procurar: "",
            userData: false
        };
    },
    methods: {
        async getUser() {
            try {
                const response = await axios.get(`https://api.github.com/users/${this.procurar}`);
                this.userData = response.data;
            } catch (error) {
                console.error("Erro ao buscar usuário:", error);
            }
        }
    }
};

</script>

<template>
    <div class="container">
        <h1>GitHub API</h1>

        <form>
            <input type="text" v-model="procurar" placeholder="Digite um usuário">
            <!-- DIRETIVA DE MODIFICADOR -->
            <button @click.prevent="getUser" type="submit">Buscar</button>
        </form>

        <!-- DIRETIVA DE RENDERIZAÇÃO -->
        <div v-if="userData" class="api">
            <div class="img">
                <img id="avatar_url" :src="userData.avatar_url" alt="Avatar do usuário">
            </div>
            <div class="informacoes">
                <h2>ID: {{ userData.id }}</h2>
                <h2>Login: {{ userData.login }}</h2>
                <h2>Nome: {{ userData.name }}</h2>
                <h2>Localização: {{ userData.location }}</h2>
            </div>
        </div>  
    </div>
</template>

<style>
.container {
    width: 100%;
    height: 100vh;

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.api {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 70px;
    margin-top: 70px;
}

.informacoes {
    display: flex;
    flex-direction: column;
}

h2 {
    text-align: left;
    margin-bottom: 30px;
}

input {
    width: 200px;
    height: 40px;

    padding-left: 10px;
    margin-right: -5px;
    border-radius: 5px 0 0 5px;
    outline: none;
}

button {
    width: 100px;
    height: 40px;
    border-radius: 0 5px 5px 0;
    cursor: pointer;
}

#avatar_url {
    border-radius: 50%;
}
</style>