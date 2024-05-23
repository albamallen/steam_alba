<template>
    <article>
     <img :src="`https://picsum.photos/500/30${user.id}`" :alt="user.name.firstname">
     <div>
        <p>{{user.username}}</p>
        <p>{{user.password}}</p>
     </div>
    </article>
 </template>
 
 <script setup>
 const props = defineProps({
     user:{
         type: Object,
         requiered: false
     }
 });
 const { user } = props;
 </script>