<template>
<div id="app">
  <div class="header">
    <img src="/images/Banner.png">
  </div>
  <div class="content">
    <router-view />
  </div>
  <div class="footer">
    <router-link to="/admin">Admin</router-link>
  </div>
</div>
</template>

<style>
html {
  box-sizing: border-box;
}

body {
  font-family: 'Montserrat', sans-serif;
  font-size: 16px;
  background: #fff;
  background-color: #CEE3FF;
  padding: 0px;
  margin: 0px;
}

/* Header */
.header img{
  width: 100%;
  height: auto;
}

.title {
  margin-top: 5px;
}

.title h1 {
  font-size: 30px;
}

.content {
  padding: 20px 100px;
  min-height: 500px;
}

/* Footer */
.footer {
  height: 50px;
  padding: 20px 100px 0px 100px;
  background: #FFBCBA;
  font-size: 12px;
  text-align: center;
}

.footer a {
  color: white;
}

h1 {
  font-size: 20px;
}

h2 {
  font-size: 14px;
}
</style>
