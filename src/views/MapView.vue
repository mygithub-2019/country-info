<template>
    <div class="col-lg-12"><br>
        <div id="regions_div" style="width: 1000px; height: 500px;"></div>
    </div>
</template>

<script>
export default {
    created(){
         google.charts.load('current', {
            'packages':['geochart'],
            // Note: you will need to get a mapsApiKey for your project.
            // See: https://developers.google.com/chart/interactive/docs/basic_load_libs#load-settings
            'mapsApiKey': 'AIzaSyD-9tSrke72PouQMnMX-a7eZSW0jkFMBWY'
        });
      google.charts.setOnLoadCallback(drawRegionsMap);

      function drawRegionsMap() {
        var data = google.visualization.arrayToDataTable([
          ['Country', 'Popularity'],
          ['China', 1377422166],
          ['India', 1295210000],
          ['USA', 323947000],
          ['Indonesia', 258705000],
          ['Brazil', 206135893],
          ['Pakistan', 194125062],
          ['Nigeria', 186988000],
          ['Bangladesh', 161006790],
          ['Russian', 146599183],
          ['Australia', 24117360],
          ['Canada', 36155487],
          ['Iran', 79369900]
        ]);

        var options = {};

        var chart = new google.visualization.GeoChart(document.getElementById('regions_div'));

        chart.draw(data, options);
      }
    }
}
</script>
