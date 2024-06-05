<template>
  <div>
    <NavBar />
    <NuxtPage />
    <!-- <Footer /> -->
  </div>
</template>

<style lang="postcss">
:root{
  --primary: #00FF03;
  --700: #E6E6E6;
  --300: #6C6C6C;
  --100: #151615;
}
h1{
  font-family: Roboto;
  font-size: 60px;
  font-weight: 700;
}
h2{
  font-family: Roboto;
  font-size: 40px;
  font-weight: 700;
}
h3{
  font-family: Roboto;
  font-size: 30px;
  font-weight: 400;
}
h4{
  font-family: Roboto;
  font-size: 22px;
  font-weight: 400;
}
h5{
  font-family: Roboto;
  font-size: 18px;
  font-weight: 400;
}
p{
  font-family: Roboto;
  font-size: 16px;
  font-weight: 100;
}
.sec-text{
  font-family: DM mono;
  font-size: 16px;
  color: var(--primary);
}
.sec-p{
  font-family: DM mono;
  font-size: 16px;
}


  *{
    box-sizing: border-box; 
    font-family: 'DM Mono', monospace;
    font-family: Roboto;
  }
  .containert{
    @apply p-8;
  } 

/* Estilos para dispositivos con un ancho máximo de 480px (típicamente móviles) */
@media (max-width: 480px) {
  h1 {
    font-size: 30px;
  }
  h2{
    font-size: 20px;
  }
  h3{
    font-size: 15px;
  }
  h4{
    font-size: 25px;
  }
  h5{
    font-size: 12px;
  }
  p{
    font-size: 10px;
  }
  .sec-text{
    font-size: 10px;
  }
  .sec-p{
    font-size: 10px;
  }
}

</style>