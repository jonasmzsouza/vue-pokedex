<template>
  <div class="container">
    <div class="row mt-2">
      <div class="col mb-2">stage</div>

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
            <div class="card-pokemon bg-gram">
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
};
</script>

<style>
body {
  background-color: #dee3eb;
}
</style>

<style scoped>
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

.bg-fogo {
  background-color: #e47373;
}

.bg-agua {
  background-color: #5a9ed2;
}

.bg-inseto {
  background-color: #26d3ab;
}

.bg-normal {
  background-color: #cecece;
}
</style>
