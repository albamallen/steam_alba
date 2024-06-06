 <template>
  <div class="modal-overlay" @click.self="closeModal">
    <div class="modal-wrapper">
      <div class="modal-content">
        <button class="close-button" @click="closeModal"><ButtonGris :showIcon="true" IconName="line-md:close" /></button>
        <h2 class="modal-title h2">Inicia sesión en Steam</h2>
        <div class="form-group">
          <input class="sec-p" type="text" id="username" v-model="username" placeholder="Usuario">
        </div>
        <div class="form-group">
          <input class="sec-p" type="password" id="password" v-model="password" placeholder="Password">
        </div>
        <div class="button-group">
          <Button buttonText="Login" @click="emitLogin"/>
        </div>
        <div class="button-group">
          <ButtonGris :showText="true" buttonText="Crear cuenta" @click="emitOpenSignup"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Button from '../components/Button.vue';
import ButtonGris from '../components/ButtonGris.vue';

export default {
  components: {
    Button,
    ButtonGris
  },
  data() {
    return {
      username: '',
      password: ''
    };
  },
  methods: {
    emitLogin() {
      this.$emit('login', { username: this.username, password: this.password });
      this.username = '';
      this.password = '';
    },
    closeModal() {
      this.$emit('close');
    },
    emitOpenSignup() {
      this.$emit('openSignup');
    }
  }
};
</script>
<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 2500;
}

.modal-wrapper {
  background: var(--700);
  border-radius: 15px;
  border: 2px var(--100) solid;
  padding: 40px;
}

.modal-content {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.close-button {
  align-self: flex-end;
  background-color: transparent;
  border: none;
  cursor: pointer;
  font-size: 24px;
}

.modal-title {
  text-align: center;
  color: var(--100);
}

.form-group {
  display: flex;
  flex-direction: column;
}

label {
  color: var(--300);
  font-size: 16px;
  font-family: SF Mono;
  font-weight: 400;
}

input {
  padding: 10px;
  border-bottom: 1px solid var(--100);

}

.button-group {
  display: flex;
  justify-content: center;
}

.primary-button {
  background: var(--primary);
  color: var(--100);
  border: none;
  border-radius: 45px;
  padding: 10px 30px;
  cursor: pointer;
}

.secondary-button {
  background: var(--700);
  color: var(--300);
  border: none;
  border-radius: 41px;
  padding: 10px 30px;
  cursor: pointer;
}
</style>