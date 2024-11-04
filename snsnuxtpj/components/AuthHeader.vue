<!-- Please remove this file from your project -->
<template>
  <header class="header">
    <div class="header__inner">
      <a href="/" class="header__logo-link">
        <img :src="logo" alt="SHARE" class="header__logo">
      </a>
      <nav class="header__nav">
        <ul class="header__nav-list">
          <li class="header__nav-list-item">
            <a href="/register" class="header__nav-list-link">新規登録</a>
          </li>
          <li class="header__nav-list-item">
            <a href="/login" class="header__nav-list-link">ログイン</a>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      logo: require('@/assets/images/logo.png')
    }
  }
}
</script>

<style>
  .header{
    background: #17202a;
    padding: 0 20px;
    width: 100%;
    height: 70px;
  }
  .header__inner{
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .header__logo{
    width: 125px;
  }
  .header__nav-list{
    display: flex;
    justify-content: flex-end;
    list-style: none;
  }
  .header__nav-list-item{
    margin-left: 1em;
    list-style: none;
  }
  .header__nav-list-link{
    color: #fff;
    text-decoration: none;
  }
</style>
