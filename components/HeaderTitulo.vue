<template>
    <div class="Frame247">
      <div class="Titulo">{{ title }}</div>
      <div class="Floatingnav">
        <ButtonGris :showIcon="true" IconName="ic:baseline-language"/>
        <ButtonGris :showIcon="true" IconName="line-md:search"/>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      title: {
        type: String,
        default: "Titulo" // Si no se proporciona un título, se usará "Titulo" por defecto
      }
    }
  };
  </script>
  
  <style scoped>
  .Frame247 {
    width: 100%;
    height: 140px;
    justify-content: space-between;
    align-items: center;
    display: inline-flex;
    padding: 42px;
  }
  
  .Titulo {
    width: 502px;
    color: #151615;
    font-size: 40px;
    font-family: Neue Haas Grotesk Text Pro;
    font-weight: 500;
    word-wrap: break-word;
  }
  
  .Floatingnav {
    padding-left: 45px;
    padding-right: 45px;
    padding-top: 30px;
    padding-bottom: 30px;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 30px;
    display: flex;
  }
  
  .BttIconLanguage,
  .BttIconSearch {
    width: 80px;
    height: 80px;
    padding: 10px 20px;
    background: #D5D5D5;
    border-radius: 41px;
    justify-content: center;
    align-items: center;
    display: flex;
  }
  
  .Icons {
    width: 51.90px;
    height: 51.90px;
    position: relative;
  }
  
  .BoundingBox {
    width: 51.90px;
    height: 51.90px;
    left: 0px;
    top: 0px;
    position: absolute;
    background: #D9D9D9;
  }
  
  .Language,
  .Search {
    width: 41.70px;
    height: 41.64px;
    left: 5.10px;
    top: 5.13px;
    position: absolute;
    background: #151615;
  }
  </style>
  