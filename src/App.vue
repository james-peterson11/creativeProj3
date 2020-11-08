<template>
<div id="app">
  <div id="menu">
    <div id="brand">
      <router-link to="/">
        <img src="/images/apiImg.jpg">
        <p>HOME</p>
      </router-link>
    </div>
    <div id="side">
      <router-link to="/browse">
        <div class="menu-item browse">
          <img src="/images/stormy_mountain_back.jpg">
          <p>DefunctAPI</p>
        </div>
      </router-link>
      <router-link to="/smthn">
        <div class="menu-item">
          <img src="/images/apiPokeShrug.jpg">
          <p>ThrdPage</p>
        </div>
      </router-link>
    </div>
  </div>
  <router-view />
  <div id="footer">
      <p>Page Author: James Peterson</p>
      <p><a href="https://github.com/james-peterson11/creativeProj3.git">GitHub Repository</a></p>
  </div>
</div>
</template>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 50px 100px;

}

#menu {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-column-gap: 5px;
  grid-template-areas: "none brand side";
  margin-bottom: 50px;
}

#menu a {
  color: #B84901;
}

#brand {
  grid-area: brand;
  display: flex;
  justify-content: center;
}

#brand img {
  height: 200px;
}

#side {
  grid-area: side;
  display: flex;
  justify-content: flex-end;
}

#side img {
  height: 100px;
}

.menu-item {
  display: flex;
  flex-direction: column;
}

.menu-item p {
  margin: 0px;
}

.browse {
  margin-right: 50px;
}

#footer {
  display: flex;
  flex-shrink: 0;
  height: 50px;
  width: 100%;
  color: #020E14;
  flex-direction: row;
  justify-content: space-around;
  background-color: #D3BEB5;
}
</style>
