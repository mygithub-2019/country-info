<template>
    <div class="container">
        <h4>{{currentCountry}} {{ title }}</h4><hr>
        <div class="row">
            <div class="col-lg-4" style="height: 500px; overflow: auto;">
                <div class="list-group">
                    <div class="list-group-item"
                        v-for="(country, index) in COUNTRIES" 
                        v-bind:key = 'index'   
                        @click="selectedCountry(index)">
                            <div class='row' @click="loadNews(country)">
                                <div class='col-xs-4 logo' :id='index'>
                                    <div class='data'>
                                        {{country.alpha2Code}}
                                    </div>
                                </div>&nbsp;
                                <div class='col-xs-6 text-overflow'>{{country.name}}
                                </div>
                                <div class='col-xs-2'>
                                    <img :src="country.flag" alt="Smiley face" height="30" width="42">
                                </div>
                            </div>
                    </div>
                </div>
            </div>
            <div class="col-lg-8" style="height: 500px; overflow: auto;">
                <app-Loader v-if="isLoading"></app-Loader>
                <div v-if="noNews && !isLoading">Sorry, we didn't find any latest news...!</div>
                <div v-if="!noNews">
                    <div 
                        v-for="(article, index) in articles"
                        v-bind:key = 'index'>
                        <!-- <h4>{{article.title}}</h4>
                        <h6>{{article.description}}</h6>
                        <p>{{article.content}}</p> -->
                        <app-news-detail-page :newsInfo=article></app-news-detail-page>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import Loader from '../components/Loader'
import NewsDetailPage from './NewsDetailPage.vue'

export default {
    data(){
        return{
            title: 'Latest News',
            articles: [],
            api_key: 'c1e973ef022d44b494f164f57d055a88',
            noNews: true,
            isLoading: false,
            currentCountry: ""
        }
    },
    methods : {
        loadNews(country){
            this.currentCountry = country.name
            this.isLoading = true
            this.articles = []
            let url = `https://newsapi.org/v2/top-headlines?country=${country.alpha2Code}&apiKey=${this.api_key}`
            axios
                .get(url)
                .then(response => {
                    this.articles = response.data.articles
                    this.noNews = response.data.articles.length <= 0 ? true : !this.noNews
                    this.isLoading = false
                })
                .catch(error => {
                    console.log(error)
                })
            },
            selectedCountry(index) {
                this.resetSelectedCountry()
                const _element = document.getElementById(index)
                _element.style.backgroundColor = "#60a9e8";
                _element.style.color = "black";
                document.getElementsByClassName(_element.parentElement.parentElement.className)[index].style.borderLeft = "5px solid #107aec96";
            },
            resetSelectedCountry() {
                for(let i=0; i<this.$props.COUNTRIES.length; i++){
                    const _elementRef = document.getElementById(i)
                    _elementRef.style.backgroundColor = "";
                    _elementRef.style.color = "";
                    document.getElementsByClassName(_elementRef.parentElement.parentElement.className)[i].style.borderLeft = "";
                }
            }
    },
    props: ([
        'COUNTRIES'
    ]),
    components: {
        appLoader: Loader,
        appNewsDetailPage: NewsDetailPage
    }
}
</script>
<style lang="scss" scoped>
.logo{
	margin-left: 5px;
	width: 40px;
    height: 40px;
    border: 1px solid #ccc7c7;
    color: #716c6c;
    border-radius: 50%;
    box-shadow: 2px 1px 4px 0px;
}
.data {
    margin-top: 7px;
}
.text-overflow {
    white-space: nowrap;
    width: 210px;
    overflow: hidden;
    text-overflow: ellipsis;
}
.list-group-item {
    cursor: pointer;
}
img {
    opacity: 0.9;
}
</style>
