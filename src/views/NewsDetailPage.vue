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
                        <img :src="newsInfo.urlToImage" alt="Image not provided" height="150" width="300">
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
</style>

