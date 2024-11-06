<template>
  <div id="app">
    <AuthHeader/>
    <main class="main-contents">
      <div class="register">
        <div class="inner">
          <div class="register__block">
            <h1 class="register__ttl">新規登録</h1>
            <!-- <form action="" class="register-form"> -->
              <validation-observer ref="obs" v-slot="ObserverProps">
                <div class="regirster-form__item">
                  <validation-provider v-slot="{ errors }" rules="required">
                    <input type="text" name="name" placeholder="ユーザーネーム" class="register-form__input" v-model="newName">
                    <div class="error">{{ errors[0] }}</div>
                  </validation-provider>
                </div>
                <div class="regirster-form__item">
                  <validation-provider v-slot="{ errors }" rules="required|email">
                    <input type="email" name="email" placeholder="メールアドレス" class="register-form__input" v-model="newEmail">
                    <div class="error">{{ errors[0] }}</div>
                  </validation-provider>
                </div>
                <div class="regirster-form__item">
                  <validation-provider v-slot="{ errors }" rules="required|min:8|alpha_dash">
                    <input type="password" name="password" placeholder="パスワード" class="register-form__input" v-model="newPassword">
                    <div class="error">{{ errors[0] }}</div>
                  </validation-provider>
                </div>
                <button @click="registerUser" type="button" :disabled="ObserverProps.invalid || !ObserverProps.validated">新規登録</button>
              </validation-observer>
            <!-- </form> -->
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

      const isValid = await this.$refs.obs.validate();
      if(!isValid) {
        return; //バリデーション失敗時は処理を中止
      }

      const sendData = {
        name: this.newName,
        email: this.newEmail,
        password: this.newPassword,
      }

      try{
        await this.$axios.post("http://127.0.0.1:8000/api/register/", sendData);
        this.$toast.success("登録に成功しました");
        this.$router.push('/login');
      } catch(error) {
        this.$toast.error("登録に失敗しました: " + error.response.data.message);
      }
    }
  }
 }
</script>

<style>
.error {
  color: red;
}
</style>
