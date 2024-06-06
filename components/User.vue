<template>
  <div class="Pointcard">
    <div class="Frame158">
      <div class="Frame160">
        <div class="Img">
          <img :src="`https://picsum.photos/232/232?random=${user.id}`" :alt="user.username" />
        </div>
      </div>
    </div>
    <h3 class="NombreDelUsuario">{{ user.username }}</h3>
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
  flex-direction: column;
  justify-content: center;
  align-items: center;
  display: flex;
}

.NombreDelUsuario {
  word-wrap: break-word;
}
@media (max-width: 480px) {
  .Img{
    width: 100px;
    height: 100px;
  }
}
</style>