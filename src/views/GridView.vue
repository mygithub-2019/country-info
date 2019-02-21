<template>
    <div class="">
        <div class=""
            v-for="(country, index) in COUNTRIES" 
            v-bind:key = 'index'>
            <!-- <div class="c-card">
                <img :src="country.flag" alt="Smiley face" height="50%" width="100%">
                <div class="card" style="float: right;">
                    <p class="card-text">
                        <strong>{{ country.name }}<small>({{ country.alpha3Code}})</small> - {{ country.nativeName }}</strong>
                    </p>
                    <span>Capital- {{ country.capital}}</span>
                    <span>Region- {{ country.region}}</span>
                    <p>Sub Region- {{ country.subregion }}</p>
                    <a href="" data-toggle="modal" data-target="#myModal">more...</a>
                </div>
            </div> -->
            <div class="card" style="float: left;width: 350px;height: 300px;margin: 5px;">
                <div class="card-header">
                    <img :src="country.flag" :alt="country.name" :title="country.name">
                    <!-- <h6 class="card-title">{{ country.name }}</h6> -->
                    <p class="card-title">
                        <strong>{{ country.name }} <sup>({{ country.alpha3Code}})</sup></strong>
                        <sub>Region- {{ country.region}}</sub>
                    </p>
                </div>
                <div class="card-body">
                    
                    <p><strong>Capital</strong>- {{ country.capital}}</p>
                    <!-- <p>Region- {{ country.region}}</p> -->
                    <p><strong>Sub Region</strong>- {{ country.subregion }}</p> 
                    <p><strong>Currency</strong>- {{country.currencies[0].name}}
                                <sup>( {{country.currencies[0].code}}-{{country.currencies[0].symbol}} )</sup>
                    </p>
                    <a href="" data-toggle="modal" data-target="#myModal">more...</a> 
                </div> 
                <div class="card-footer">
                    <a v-bind:href="'https://en.wikipedia.org/wiki/'+country.name"
                        target="blank">Wiki</a>
                </div>
            </div>

            <!-- Modal content-->
            <div class="modal fade" id="myModal" role="dialog">
                <div class="modal-dialog">
                    <!-- Modal content-->
                    <div class="modal-content">
                        <div class="modal-header">
          <h4 class="modal-title">Modal Heading</h4>
          <button type="button" class="close" data-dismiss="modal">&times;</button>
        </div>
                        <div class="modal-body">
                            <app-country-detail></app-country-detail>
                        </div>
                        <div class="modal-footer">
                        <button type="button" class="btn btn-danger" data-dismiss="modal">Close</button>
                        </div>
                    </div>
                </div>
            </div>
            
        </div>
    </div>
</template>
<script>
import CountryDetail from '../components/CountryDetail.vue'

export default {
    props: ([
        'COUNTRIES'
    ]),
    components: {
        appCountryDetail: CountryDetail
    }
}
</script>
<style lang="scss" scoped>
.card-margin {
    margin: 10px;
    border: 1px solid 1px solid rgba(0,0,0,.125)
}
img{
    border-radius: 50%;
    height: 100%;
    width: 12%;
    float: left;
}
.c-card{
    width: 50%;
    height: 50%;
    border: 1px solid gray
}
</style>
