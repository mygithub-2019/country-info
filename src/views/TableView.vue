<template>
    <div class="col-lg-12"><br>
        <table class="table table-hover table-dark">
            <thead>
                <tr>
                <th scope="col">#</th>
                <th scope="col">Flag</th>
                <th scope="col" @click="sort('name')">Country Name 
                    <i v-if='currentSortDir == "asc"' class="fa fa-arrow-up" aria-hidden="true"></i>
                    <i v-if='currentSortDir != "asc"' class="fa fa-arrow-down" aria-hidden="true"></i>
                </th>
                <th scope="col" @click="sort('capital')">Capital
                    <i v-if='currentSortDir == "asc"' class="fa fa-arrow-up" aria-hidden="true"></i>
                    <i v-if='currentSortDir != "asc"' class="fa fa-arrow-down" aria-hidden="true"></i>
                </th>
                <th scope="col" @click="sort('region')">Region
                    <i v-if='currentSortDir == "asc"' class="fa fa-arrow-up" aria-hidden="true"></i>
                    <i v-if='currentSortDir != "asc"' class="fa fa-arrow-down" aria-hidden="true"></i>
                </th>
                <th scope="col" @click="sort('alpha3Code')">Country Code
                    <i v-if='currentSortDir == "asc"' class="fa fa-arrow-up" aria-hidden="true"></i>
                    <i v-if='currentSortDir != "asc"' class="fa fa-arrow-down" aria-hidden="true"></i>
                </th>
                <th scope="col" @click="sort('numericCode')">Phone Code
                    <i v-if='currentSortDir == "asc"' class="fa fa-arrow-up" aria-hidden="true"></i>
                    <i v-if='currentSortDir != "asc"' class="fa fa-arrow-down" aria-hidden="true"></i>
                </th>
                <th scope="col" @click="sort('population')">Population
                    <i v-if='currentSortDir == "asc"' class="fa fa-arrow-up" aria-hidden="true"></i>
                    <i v-if='currentSortDir != "asc"' class="fa fa-arrow-down" aria-hidden="true"></i>
                </th>
                </tr>
            </thead>
            <tbody style="height: 500px;">
                <tr v-for="(country, index) in sortedCountries" v-bind:key = 'index'>
                    <th scope="row">{{ index + 1 }}</th>
                    <td>
                        <img :src="country.flag" alt="Smiley face" height="30" width="42">
                    </td>
                    <td>{{ country.name }}</td>
                    <td>{{ country.capital }}</td>
                    <td>{{ country.region}}</td>
                    <td>{{ country.alpha3Code}}</td>
                    <td>{{ country.numericCode}}</td>
                    <td>{{ country.population.toLocaleString() }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script>
export default {
    data(){
        return {
            currentSort:'name',
            currentSortDir:'asc'
        }
    },
    props: ([
        'COUNTRIES'
    ]),
    methods:{
        sort:function(sortBy) {
            //if s == current sort, reverse
            if(sortBy === this.currentSort) {
            this.currentSortDir = this.currentSortDir==='asc'?'desc':'asc';
            }
            this.currentSort = sortBy;
        }
    },
    computed:{
        sortedCountries:function() {
            return this.$props.COUNTRIES.sort((a,b) => {
                let modifier = 1;
                if(this.currentSortDir === 'desc') modifier = -1;
                if(a[this.currentSort] < b[this.currentSort]) return -1 * modifier;
                if(a[this.currentSort] > b[this.currentSort]) return 1 * modifier;
                return 0;
            });
        }
    }
}
</script>
