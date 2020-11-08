<template>
<div>
<h2>DIV CLASS 1!</h2>
  <div class="text">
    <p>Insert stuff here that applies to this slide</p>
  </div>
  <div id="outline">
  <p>Look! One picture stays awkwardly spaced away from the others in any non
  mobile view!</p>
    <div id ="one">
      <img src="/images/old_goji3.png">
    </div>
    <div id ="two">
      <img src="/images/old_goji2.jpg">
    </div>
    <div id ="three">
      <img src="/images/old_goji.jpg">
    </div>
  </div>
</div>
</template>

<style>
* {
  box-sizing: border-box;

}

body {
  margin: 50px 100px;
  background-color: #D3EAF5;

}

#outline {
  background-color: #D3EAF5;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-column-gap: 5px;
  grid-template-areas: "one two three";
  margin-bottom: 50px;
}


#one {
  grid-area: one;
  display: flex;
  justify-content: center;
}

#one img {
  height: 200px;
}

#two {
  grid-area: two;
  display: flex;
  justify-content: flex-end;
}

#two, img {
  height: 200px;
}

#three {
  grid-area: three;
  display: flex;
  justify-content: flex-front;
}

#three, img {
  height: 200px;
}

.browse {
  margin-right: 50px;
}

</style>
