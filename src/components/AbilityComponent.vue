<template>
  <div>
    <div v-if="!pokemon.abilities">Select a pokemon</div>
    <div v-else>
      <table class="table text-white">
        <tbody>
          <tr v-for="(ability, index) in pokemon.abilities" :key="index">
            <td>{{ ability }}</td>
            <td class="d-flex justify-content-end">
              <button type="button" class="btn btn-danger btn-sm">x</button>
            </td>
          </tr>
        </tbody>
      </table>
      <input type="text" class="form-control" placeholder="Add ability" />
    </div>
  </div>
</template>

<script>
export default {
  name: "AbilityComponent",
  props: {
    pokemon: Object,
  },
};
</script>

<style scoped>
.table td {
  border: none;
  color: white;
  background: transparent;
}
</style>
