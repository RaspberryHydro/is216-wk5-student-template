<script setup>
import { ref } from 'vue'
const items = ref(['keyboard', 'mouse', 'iPhone', 'macbook', 'adapter'])
const newitem = ref('');
// TODO: Add Code Here

function delitem(key)
{
items.value.splice(key,1);
}
function addItem(l)
{
    items.value.push(l);
    newitem.value="";
}
</script>

<template>

    <h2>Shopping Cart</h2>
    <!-- TODO: Add Code Here -->
<ul>
    <template v-for="i,key in items">
    <li>{{ i }}<button @click="delitem(key)" style="display:inline;">delete!</button></li>
    </template>
</ul>
   <input type="text" id="in" v-model="newitem" @keyup.enter="addItem(newitem)"><button @click="addItem(newitem)" >add</button>
</template>
