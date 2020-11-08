<template>
  <div class='overCont'>
    <div class="col">
      <h1> It's a page that does nothing! Why? Because VUE overcomplicates things!</h1>


    </div>
    <div class="search">
      <form class="pure-form">
        <input type="text" v-model="search" placeholder="search"/>
        <i class="fas fa-search"></i><input v-model="searchText" />
        <button class="btnClass">Search</button>
        <button v-on:click="bOnClick">AGAIN</button>
      </form>
    </div>
    <div class='col2'>
        <p>Yeah, no seriously. I spent six hours trying to get a already fully functioning
        piece of code (from a previous project) working inside of vue. Simple right? It failed.
        So, the 'mock data' I was planning on gathering from it is unimplemented.</p>
        <p> (So, discretion is the better part of valor. If I get the footer working I'll be happy) </p>
        <br>
      <p id="result"></p>

    </div>
  </div>
</template>

<script>
export default {
  name: 'Browse',
  components: {

  },
  data() {
    return {
      searchText: '',
      search:"",
      results:[]
    }
  },
  methods: {
    bOnClick: function(event) {
      onClick();
      if (event) {
       alert(event.target.tagName)
     }
    }
  }
}
  function onClick() {
    //e.preventDefault();
    // get form values

    //var txt = document.getElementById('searchText');
    //if(txt) {
    //  let number = txt.value;
    //}
    let number = document.getElementById('searchText').value;
    //let s = document.getElementById('selector');
    //let type = s.options[s.selectedIndex].value;

    // check if number is empty
    if (number === "") {
      number = "blastoise|charizard";
    }

    // setup URL
    //https://api.pokemontcg.io/<version>/<resource>
    //https://api.pokemontcg.io/v1/cards?name=blastoise|charizard
    let url = "https://api.pokemontcg.io/v1/cards?name=" + number;
    // call API
    fetch(url)
      .then(function(response) {
        // make sure the request was successful
        if (response.status != 200) {
          return {
            text: "Error calling the Numbers API service: " + response.statusText
          }
        }
        //console.log(response);
        return response.json();
      }).then(function(json) {

        // update DOM with response
        console.log(json);
        let results = "";
        for (let j = 0; j < 3; j++) {
          results += '<h2>Pokemon: ' + json.cards[j].name + "</h2>";
          results += '<img src = "' + json.cards[j].imageUrl + '"/>';
          for (let i=0; i < json.cards[j].attacks.length; i++) {
            results += '<p> Attack: ' + json.cards[j].attacks[i].name + '</p>';
             //results += '<img src="http://openweathermap.org/img/w/' + json.weather[i].icon + '.png"/>';
          }
        }

        updateResult(results);
        //document.getElementById("result").innerHTML = results;
      });
  }

function updateResult(info) {
//document.getElementById('result').textContent = info;
this.$root.$data.results = info;
}

  //This makes sure the value isn't null before adding the listener
  var check = document.getElementById('btnClass');
  if(check) {
    check.addEventListener('click', onClick);
  }

</script>
