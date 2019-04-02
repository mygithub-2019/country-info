<template>
      <!-- Modal content-->
    <div class="modal-content">
      <div class="modal-header">
        <img :src='propCuntryData.flag'/> &nbsp;&nbsp;
        <h4 class="modal-title">{{ propCuntryData.name }}</h4>
        <button type="button" class="close" data-dismiss="modal">&times;</button>
      </div>
      <div class="modal-body">
        <table>
          <tr>
            <td><strong class="text-label-float"> Name:</strong></td>
            <td class="text-content-float"> {{ propCuntryData.nativeName}}</td>
          </tr>
          <tr>
            <td><strong class="text-label-float">Area:</strong></td>
            <td class="text-content-float"> {{ propCuntryData.area}}</td>
          </tr>
          <tr>
            <td><strong class="text-label-float">Capital:</strong></td>
            <td class="text-content-float"> {{ propCuntryData.capital}}</td>
          </tr>
          <tr>
            <td><strong class="text-label-float">Demonym:</strong></td>
            <td class="text-content-float"> {{ propCuntryData.demonym}}</td>
          </tr>
          <tr>
            <td><strong class="text-label-float">Population:</strong></td>
            <td class="text-content-float"> {{ propCuntryData.population}}</td>
          </tr>
          <tr>
            <td><strong class="text-label-float">Region:</strong></td>
            <td class="text-content-float"> {{ propCuntryData.region}}</td>
          </tr>
          <tr>
            <td><strong class="text-label-float">Subregion:</strong></td>
            <td class="text-content-float"> {{ propCuntryData.subregion}}</td>
          </tr>
          <tr>
            <td><strong class="text-label-float">Timezones:</strong></td>
            <td class="text-content-float"> {{ propCuntryData.timezones}}</td>
          </tr>
        </table>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-danger" data-dismiss="modal">Close</button>
      </div>
    </div>
</template>
<script>
export default {
  props:[
    'propCuntryData'
  ]
}
</script>

<style lang="scss" scoped>
.content {
    width: 50%;
    height: 20%;
    border: 1px solid red;
}
img {
  width: 50px;
  height: 50px;
  border-radius: 50px;
}
.text-label-float{
  float: right;
}
.text-content-float{
  float: left;
}
</style>

