<template>
  <div id="app">
    <AuthHeader/>
    <main class="main-contents">
      <div class="register">
        <div class="inner">
          <div class="register__block">
            <h1 class="register__ttl">新規登録</h1>
            <form action="" class="register-form">
              <div class="regirster-form__item">
                <input type="text" name="name" placeholder="ユーザーネーム" class="register-form__input" v-model="newName">
              </div>
              <div class="regirster-form__item">
                <input type="email" name="email" placeholder="メールアドレス" class="register-form__input" v-model="newEmail">
              </div>
              <div class="regirster-form__item">
                <input type="password" name="password" placeholder="パスワード" class="register-form__input" v-model="newPassword">
              </div>
              <button @click="registerUser">新規登録</button>
            </form>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newName: "",
      newEmail: "",
      newPassword: "",
    }
  },
  methods: {
    async registerUser() {
      const sendData = {
        name: this.newName,
        email: this.newEmail,
        password: this.newPassword,
      }
      await this.$axios.post("http://127.0.0.1:8000/api/contact/", sendData);

    }
  }
 }
</script>
