<template>
    <div class="Pointcard">
      <div class="Frame158">
        <div class="Frame160">
          <div class="Img">
            <img :src="`https://picsum.photos/232/232?random=${user.id}`" :alt="user.username" />
          </div>
        </div>
      </div>
      <div class="NombreDelUsuario"><p>{{ user.username }}</p></div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      user: {
        type: Object,
        required: true
      }
    }
  };
  </script>

  
  <style scoped>
  .Pointcard {
    width: 271px;
    height: 281.05px;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 12px;
    display: inline-flex;
  }
  
  .Frame158 {
    justify-content: center;
    align-items: center;
    gap: 10px;
    display: inline-flex;
  }
  
  .Frame160 {
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    display: inline-flex;
  }
  
  .Img {
    width: 232.05px;
    height: 232.05px;
    border-radius: 142px;
    overflow: hidden;
    border: 3px black solid;
    background-image: url('https://via.placeholder.com/232x232');
    flex-direction: column;
    justify-content: center;
    align-items: center;
    display: flex;
  }
  
  .Image59 {
    width: 464.10px;
    height: 232.05px;
  }
  
  .NombreDelUsuario {
    color: black;
    font-size: 30px;
    font-family: Neue Haas Grotesk Text Pro;
    font-weight: 500;
    word-wrap: break-word;
  }
  </style>
  