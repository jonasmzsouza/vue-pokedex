<template>
  <div class="container">
    <div class="row mt-2">
      <!-- start left side -->
      <div class="col mb-2">
        <div class="card stage">
          <div class="card-header"></div>

          <div class="card-body bg-pokeball bg-normal">
            <div class="pokemon">
              <!-- 
                name="jump" //indicates the set of classes
                type="animation" //predominant progression time
                :duration="{ enter: 2000, leave: 1000 }" //manual progression time
              -->
              <transition
                enter-active-class="animate__animated animate__bounceIn"
                leave-active-class="animate__animated animate__bounceOut"
              >
                <img src="@/assets/images/pokemons/001.png" v-if="show" />
              </transition>

              <div class="evolutions">
                <transition name="fade">
                  <img src="@/assets/images/pokemons/002.png" v-if="show" />
                </transition>
                <transition name="fade">
                  <img src="@/assets/images/pokemons/003.png" v-if="show" />
                </transition>
              </div>
            </div>
          </div>

          <div class="card-footer">
            <nav class="nav nav-pills nav-fill">
              <!-- navigation menu -->
            </nav>

            <div class="details">
              <!-- displays data according to navigation menu -->
            </div>
          </div>
        </div>
      </div>
      <!-- end left side -->

      <!-- start right side -->
      <div class="col mb-2 pokedex">
        <div class="row">
          <div class="col">
            <h1>Pokedex</h1>
          </div>
        </div>

        <div class="row">
          <div class="col">
            <select class="form-select">
              <option>increasing id</option>
              <option>decreasing id</option>
              <option>A-Z</option>
            </select>
          </div>

          <div class="col">
            <input
              type="text"
              class="form-control"
              placeholder="search pokemon"
            />
          </div>
        </div>

        <div class="row">
          <div class="pokedex-catalog">
            <!-- start of dynamic list -->
            <div class="card-pokemon bg-gram" @click="show = !show">
              <h1>1 Bulbasaur</h1>
              <span>gram</span>
              <div class="card-pokemon-img">
                <img src="@/assets/images/pokemons/001.png" />
              </div>
            </div>
            <!-- end of dynamic list -->
          </div>
        </div>
      </div>
      <!-- end right side -->
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeView",
  data: () => ({
    show: false,
  }),
};
</script>

<style>
body {
  background-color: #dee3eb;
}
</style>

<style scoped>
@import "~@/assets/css/animations.css";

.pokedex {
  padding: 20px;
  background-color: #ffffff;
  -webkit-box-shadow: 2px 2px 10px rgba(200, 200, 200, 0.77);
  -moz-box-shadow: 2px 2px 10px rgba(200, 200, 200, 0.77);
  box-shadow: 2px 2px 10px rgba(200, 200, 200, 0.77);
  border-radius: 10px;
}

.pokedex-catalog {
  overflow: auto;
  display: flex;
  flex-wrap: wrap;
  height: 400px;
  width: 98%;
  margin-top: 10px;
}

.card-pokemon {
  position: relative;
  margin: 5px;
  width: 150px;
  height: 115px;
  cursor: pointer;
  border-radius: 5px;
  -webkit-box-shadow: 2px 2px 2px rgba(200, 200, 200, 0.77);
  -moz-box-shadow: 2px 2px 2px rgba(200, 200, 200, 0.77);
  box-shadow: 2px 2px 2px rgba(200, 200, 200, 0.77);
}

.card-pokemon h1 {
  color: #fff;
  font-size: 14px;
  margin: 5px 0px 0px 5px;
  padding: 0px;
}

.card-pokemon span {
  color: #fff;
  position: absolute;
  background: rgba(255, 255, 255, 0.3);
  font-size: 12px;
  margin: 10px 0px 0px 5px;
  padding: 5px 10px 5px 10px;
  border-radius: 25px;
}

.card-pokemon img {
  max-width: 60%;
  max-height: 60%;
  float: right;
}

.bg-gram {
  background-color: #2d8f78;
}

.bg-fire {
  background-color: #e47373;
}

.bg-water {
  background-color: #5a9ed2;
}

.bg-insect {
  background-color: #26d3ab;
}

.bg-normal {
  background-color: #cecece;
}

.bg-pokeball {
  background-image: url("~@/assets/images/pokeball.png");
  background-repeat: no-repeat;
  background-position: bottom right;
}

.stage {
  color: #fff;
  background-color: #333;
  -webkit-box-shadow: 2px 2px 10px rgba(230, 223, 223, 0.77);
  -moz-box-shadow: 2px 2px 10px rgba(230, 223, 223, 0.77);
  box-shadow: 2px 2px 10px rgba(230, 223, 223, 0.77);
  border-radius: 10px;
}

.pokemon {
  display: block;
  text-align: center;
  height: 215px;
}

.details {
  margin: 20px 30px 20px 30px;
}

.evolutions {
  position: absolute;
  top: 0;
  right: 0;
  height: 70px;
}

.evolutions img {
  cursor: pointer;
  max-width: 100%;
  max-height: 100%;
  float: left;
}
</style>
