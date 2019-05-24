<template>
    <div>
        <!-- <h4>{{newsInfo.title}}</h4>
        <h6>{{newsInfo.description}}</h6>
        <p>{{newsInfo.content}}</p> -->
        <div class="card">
            <div class="card-header">
                <p>{{newsInfo.title}}</p>
            </div>
            <div class="card-body">
                <div class="row">
                    <div class="col-md-6">
                        <img :src="newsInfo.urlToImage" class='news-image' 
                        height = "150" width = "300" alt="Image not provided">
                        <p><i>{{newsInfo.description}}</i></p>
                    </div>
                    <div class="col-md-6">
                        <p>{{newsInfo.content}}</p>
                    </div>
                </div>
            </div> 
            <div class="card-footer">
                <div class="row">
                    <div class="col-md-6">
                        <strong>Publisher: </strong>
                        <i><a :href='newsInfo.url' :target="_blank">{{newsInfo.source.name}}</a></i>
                    </div>
                    <div class="col-md-6">
                        <i>At {{newsInfo.publishedAt}}</i>
                    </div>
                </div>
                 
            </div>
        </div><br>
    </div>
</template>

<script>
export default {
    data(){
        return{
            title: 'News Detail'
        }
    },
    props: ([
        'newsInfo'  
    ])
}
</script>

<style lang="scss" scoped>
.card-footer, .card-header {
    color: gray;
}
.news-image{
    border-radius: 5px;
    box-shadow: 0px 1px 3px 1px;
}
</style>

