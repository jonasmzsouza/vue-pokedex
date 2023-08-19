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
                @before-enter="beforeEnter"
                @enter="enter"
                @after-enter="afterEnter"
                @enter-cancelled="enterCancelled"
                @before-leave="beforeLeave"
                @leave="leave"
                @after-leave="afterLeave"
                @leave-cancelled="leaveCancelled"
              -->
              <transition
                @after-enter="transitionToShowEvolutions"
                @before-leave="transitionToHideEvolutions"
                enter-active-class="animate__animated animate__bounceIn"
                leave-active-class="animate__animated animate__bounceOut"
              >
                <img
                  :src="require(`@/assets/images/pokemons/${pokemon.image}`)"
                  v-if="show"
                />
              </transition>

              <div class="evolutions">
                <transition
                  name="fade"
                  v-for="e in pokemon.evolutions"
                  :key="e"
                >
                  <img
                    :src="
                      require(`@/assets/images/pokemons/${e
                        .toString()
                        .padStart(3, '0')}.png`)
                    "
                    v-if="showEvolutions"
                  />
                </transition>
              </div>
            </div>
          </div>

          <div class="card-footer">
            <nav class="nav nav-pills nav-fill">
              <!-- navigation menu -->
              <router-link
                class="nav-item nav-link text-white"
                :to="{ path: '/about' }"
                exact-active-class="active"
                >About</router-link
              >
              <router-link
                class="nav-item nav-link text-white"
                :to="{ path: '/status' }"
                exact-active-class="active"
                >Status</router-link
              >
              <router-link
                class="nav-item nav-link text-white"
                :to="{ path: '/ability' }"
                exact-active-class="active"
                >Ability</router-link
              >
            </nav>

            <div class="details">
              <!-- displays data according to navigation menu -->
              <router-view v-slot="{ Component }">
                <transition
                  enter-active-class="animate__animated animate__zoomInDown"
                >
                  <component :is="Component"></component>
                </transition>
              </router-view>
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
            <div
              v-for="p in pokemons"
              :key="p.id"
              :class="`card-pokemon bg-${p.type}`"
              @click="detectPokemon(p)"
            >
              <h1>{{ p.id }} {{ p.name }}</h1>
              <span>{{ p.type }}</span>
              <div class="card-pokemon-img">
                <img :src="require(`@/assets/images/pokemons/${p.image}`)" />
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
    showEvolutions: false,
    pokemon: {},
    pokemons: [
      {
        id: 1,
        name: "Bulbasaur",
        type: "gram",
        image: "001.png",
        evolutions: [2, 3],
      },
      {
        id: 2,
        name: "Ivysaur",
        type: "gram",
        image: "002.png",
        evolutions: [3],
      },
      {
        id: 3,
        name: "Venusaur",
        type: "gram",
        image: "003.png",
        evolutions: [],
      },
      {
        id: 4,
        name: "Charmander",
        type: "fire",
        image: "004.png",
        evolutions: [5, 6],
      },
      {
        id: 5,
        name: "Charmeleon",
        type: "fire",
        image: "005.png",
        evolutions: [6],
      },
      {
        id: 6,
        name: "Charizard",
        type: "fire",
        image: "006.png",
        evolutions: [],
      },
      {
        id: 7,
        name: "Squirtle",
        type: "water",
        image: "007.png",
        evolutions: [8, 9],
      },
      {
        id: 8,
        name: "Wartortle",
        type: "water",
        image: "008.png",
        evolutions: [9],
      },
      {
        id: 9,
        name: "Blastoise",
        type: "water",
        image: "009.png",
        evolutions: [],
      },
      {
        id: 10,
        name: "Caterpie",
        type: "insect",
        image: "010.png",
        evolutions: [11, 12],
      },
      {
        id: 11,
        name: "Metapod",
        type: "insect",
        image: "011.png",
        evolutions: [12],
      },
      {
        id: 12,
        name: "Butterfree",
        type: "insect",
        image: "012.png",
        evolutions: [],
      },
      {
        id: 13,
        name: "Weedle",
        type: "insect",
        image: "013.png",
        evolutions: [14, 15],
      },
      {
        id: 14,
        name: "Kakuna",
        type: "insect",
        image: "014.png",
        evolutions: [15],
      },
      {
        id: 15,
        name: "Beedrill",
        type: "insect",
        image: "015.png",
        evolutions: [],
      },
      {
        id: 16,
        name: "Pidgey",
        type: "normal",
        image: "016.png",
        evolutions: [17, 18],
      },
      {
        id: 17,
        name: "Pidgeotto",
        type: "normal",
        image: "017.png",
        evolutions: [18],
      },
      {
        id: 18,
        name: "Pidgeot",
        type: "normal",
        image: "018.png",
        evolutions: [],
      },
    ],
  }),
  methods: {
    detectPokemon(p) {
      if (this.pokemon.id != p.id && this.show) {
        setTimeout(() => {
          this.detectPokemon(p);
        }, 1000);
      }
      this.pokemon = p;
      this.show = !this.show;
      this.showEvolutions = !this.showEvolutions;
    },
    transitionToShowEvolutions() {
      this.showEvolutions = true;
    },
    transitionToHideEvolutions() {
      this.showEvolutions = false;
    },
  },
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
