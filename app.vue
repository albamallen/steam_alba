<template>
  <div>
    <NavBar />
    <NuxtPage />
    <Footer />
  </div>
</template>

<style lang="postcss">
:root{
  --primary: #00FF03;
}

  *{
    box-sizing: border-box; 
    font-family: 'DM Mono', monospace;
    font-family: Roboto;
  }
  h1{
    font-size: 2em;
  }
  .containert{
    @apply p-8;
  } 
</style>