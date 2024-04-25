<script setup>
import { ref } from 'vue'

const isHidden = ref(false)

function toggleHover(value) {
    this.isHidden = value;
}

</script>

<template>
    <div class="aside" @mouseover="toggleHover(true)" @mouseleave="toggleHover(false)"
        :class="{ 'abrirMenu': isHidden }">
        <ul>
            <a href="#">
                <li><i class="ri-vuejs-line"></i><span>Início</span></li>
            </a>
            <a href="#">
                <li><i class="ri-vuejs-line"></i><span>Perfil</span></li>
            </a>
            <a href="#">
                <li><i class="ri-vuejs-line"></i><span>Configurações</span></li>
            </a>
            <a href="#" >
                <li><i class="ri-vuejs-line"></i><span>Sair</span></li>
            </a>
            <a class='last' href="https://github.com/yurifsz" target="_blank">
                <li><i class="ri-code-view"></i><span>Código</span></li>
            </a>
        </ul>
    </div>
</template>

<style>
.aside {
    width: 80px;
    height: 100vh;


    display: flex;
    flex-direction: column;
    align-items: center;

    transition: .6s;
    background-color: #18c29c;
}

.aside span {
    display: none;
}

i {
    font-size: 40px;
    cursor: pointer;
}

ul {
    height: 100vh;
    list-style: none;
    padding-top: 70px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

a {
    color: rgba(235, 235, 235, 0.64);
    text-decoration: none;
}

li {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 25px;
    width: 300px;
    height: 80px;

    cursor: pointer;
}

li:hover {
    background: rgba(220, 228, 227, 0.6);
    transition: .6s;
}

span {
    font-weight: bold;
    font-size: 16px;
}

.last {
    margin-top: 160px;
}

.aside.abrirMenu {
    width: 300px;
    
}

.aside.abrirMenu ul li{
    display: flex;
    justify-content: start;
    padding-left: 25px;
}

.aside.abrirMenu span {
    display: block;
}
</style>
