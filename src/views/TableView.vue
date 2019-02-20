<template>
    <div class="col-lg-12" style="height: 500px;"><br>
        <table class="table table-hover header-fixed table-dark">
            <thead>
                <tr>
                <th scope="col">#</th>
                <th scope="col">Flag</th>
                <th scope="col">Country Name</th>
                <th scope="col">Captil</th>
                <th scope="col">Region</th>
                <th scope="col">Country Code</th>
                <th scope="col">Phone Code</th>
                <th scope="col">Population</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(country, index) in COUNTRIES" v-bind:key = 'index'>
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
    props: ([
        'COUNTRIES'
    ])
}
</script>
