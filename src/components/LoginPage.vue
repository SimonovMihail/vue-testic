<template>
  <div class="wrapper">
    <el-main class="main-container">
      <h1>Логин</h1>
      <el-form :model="form" ref="form" label-width="70px" @submit.prevent="login">
        <el-form-item
          label="Логин:"
          prop="login"
          :rules="[{ required: true, message: 'Пожалуйста, введите логин.', trigger: 'blur' }]"
        >
          <el-input v-model="form.login"></el-input>
        </el-form-item>
        <el-form-item
          label="Пароль:"
          prop="password"
          :rules="[{ required: true, message: 'Пожалуйста, введите пароль.', trigger: 'blur' }]"
        >
          <el-input type="password" v-model="form.password"></el-input>
        </el-form-item>
        <div class="button-container">
          <el-button class="button-login" type="primary" @click="login">Войти</el-button>
          <el-button class="button-move-to-register" type="button" @click="move_to_register"
            >Создать новый аккаунт</el-button
          >
        </div>
      </el-form>
    </el-main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        login: '',
        password: '',
      },
    };
  },
  methods: {
    login() {
      this.$refs.form.validate((valid) => {
        if (valid) {
          console.log('Login successful with:', this.form);
          console.log(this.username, this.password) // типа беку данные отправляю
        } else {
          console.error('Form validation failed');
          alert('Пожалуйста, заполните все необходимые поля!');
        }
      });
    },
    move_to_register() {
      this.$router.push({ name: 'RegisterPage' });
    },
  },
};
</script>

<style scoped>
html,
body {
  height: 100%;
  background-color: white;
}

.wrapper {
  display: flex;
  height: 100vh;
  justify-content: center;
  align-items: center;
}

.main-container {
  background-color: white;
  box-shadow: 5px 5px 20px black;
  max-width: 300px;
  margin: 0 auto;
  padding: 20px;
  text-align: center;
}

.button-container {
  display: flex;
  justify-content: space-between;
}
</style>
