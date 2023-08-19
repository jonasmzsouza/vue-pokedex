<template>
  <div>
    <table class="table text-white">
      <tbody>
        <tr>
          <td>Rage attack</td>
          <td class="d-flex justify-content-end">
            <button type="button" class="btn btn-danger btn-sm">x</button>
          </td>
        </tr>
        <tr>
          <td>Dodge</td>
          <td class="d-flex justify-content-end">
            <button type="button" class="btn btn-danger btn-sm">x</button>
          </td>
        </tr>
      </tbody>
    </table>
    <input
      type="text"
      class="form-control"
      placeholder="Add ability"
    />
  </div>
</template>

<style scoped>
.table td {
  border: none;
  color: white;
  background: transparent;
}
</style>
