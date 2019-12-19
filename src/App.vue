<template>
  <div>
    <div class="container" id="slogan">
      <img src="./assets/darth_vader.png" width="100" height="100" class="img-fluid mt-2 ml-3 mr-3">
       <div>
        <h1 class="mt-3">NameDarth</h1>
        <h6>Gerador de nomes com Vue.js, GraphQL e Node</h6>
      </div>
    </div>
    <hr>
    <div id="main">
      <div class="container">
        <div class="row">
          <!-- ====================== COLUNA 1: Prefixos ====================== -->
          <div class="col-md">
            <h4 class="mt-4">Prefixos <span class="badge badge-info">{{prefixes.length}}</span></h4>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li class="list-group-item" v-for="prefix in prefixes" v-bind:key="prefix">
                    {{prefix}}
                  </li>
                </ul>
                <br>
                <div class="input-group">
                  <input type="text" placeholder="Digite o prefixo" class="form-control" v-model="prefix" v-on:keyup.enter="addPrefix(prefix)">
                  <div class="input-group-append">
                    <button class="btn btn-info" v-on:click="addPrefix(prefix)">
                      <span class="fa fa-plus"></span>
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <!-- ====================== COLUNA 2: Sufixos ====================== -->
          <div class="col-md">
            <h4 class="mt-4">Sufixos  <span class="badge badge-info">{{sufixes.length}}</span></h4>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li class="list-group-item" v-for="sufix in sufixes" v-bind:key="sufix">
                    {{sufix}}
                  </li>
                </ul>
                <br>
                <div class="input-group">
                  <input type="text" placeholder="Digite o sufixo" class="form-control" v-model="sufix" v-on:keyup.enter="addSufix(sufix)">
                  <div class="input-group-append">
                    <button class="btn btn-info" v-on:click="addSufix(sufix)">
                      <span class="fa fa-plus"></span>
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-md">
            <h4 class="mt-4">Domínios <span class="badge badge-info">{{domins.length}}</span></h4>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li class="list-group-item" v-for="dominio in domins" v-bind:key="dominio">
                    {{dominio}}
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import "bootstrap/dist/css/bootstrap.css"
  import "font-awesome/css/font-awesome.css"
  import "animate.css/animate.css"

  export default {
    name: 'app',
    data: function(){
      return {
        prefix: "",
        sufix: "",
        prefixes: [],
        sufixes: [],
        domins: []
      }
    },
    methods: {
      addPrefix(prefix){
        this.prefixes.push(prefix);
        this.gerarDominios()
        this.prefix = ""
      },      
      addSufix(sufix){
        this.sufixes.push(sufix);
        this.gerarDominios()
        this.sufix = ""
      },
      gerarDominios(){
        this.domins = []
        for(const prefix of this.prefixes){
          for(const sufix of this.sufixes){
            this.domins.push(prefix + sufix)
          }
        }
      }
    }
  }
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Lato&display=swap');

#slogan{
  margin-top: 30px;
  margin-bottom: 30px;
  /* margin-left: 20px; */
  display: flex;
  font-family: 'Lato', sans-serif;

}
#main{
  background-color: #f1f1f1;
  padding-bottom: 30px;
  padding-top: 30px;
  font-family: 'Lato', sans-serif;
}
</style>
