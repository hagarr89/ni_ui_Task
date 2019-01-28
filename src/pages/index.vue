<template>
  <div class="index-page">
    <main-baner></main-baner>
    <div class="container">
    <div class="row">
      <div class="col-12">
      <filter-comp></filter-comp>
      <div class="inner-layout">
          <div class="main-content">
            <products-comp></products-comp>
          </div>
          <div class="more-contnet-container">
              <div class="more-contnet">
              <div class="articles">
                <h2>Articles</h2>
                  <div class="article-box">
                    <div class="image"></div>
                    <div class="content">
                      <h5>The Pros And Cons Of A Meal Delivery Service</h5>
                      <a href="javascript:;">read More</a>
                      </div>
                  </div>
                  <div class="article-box">
                      <div class="image"></div>
                    <div class="content">
                      <h5>The Pros And Cons Of A Meal Delivery Service</h5>
                      <a href="javascript:;">read More</a>
                      </div>
                  </div>
                  <div class="article-box">
                      <div class="image"></div>
                    <div class="content">
                      <h5>The Pros And Cons Of A Meal Delivery Service</h5>
                      <a href="javascript:;">read More</a>
                      </div>
                  </div>
              </div>
            </div>
           </div>
           <div class="delivery-service-container">
              <h2>main title</h2>
              <p class="prolog">
                When looking for the best food box delivery service, it can be challenging just knowing where to start. Whether you’re looking for a cook at home delivery service, or even a vegan recipe delivery, there are many food delivery meal kits to push you to be more adventurous in the
                kitchen. Naturally, not everyone has the time to plan, prepare and cook their meals from scratch, so finding the best home meal kits can really help you to become a culinary genius in the kitchen with minimal effort.
              </p>
              <div class="delivery-service" v-for="k in 4" :key="`service${k}`">
                  <h3>title</h3>
                   <p class="prolog">
                  When looking for the best food box delivery service, it can be challenging just knowing where to start. Whether you’re looking for a cook at home delivery service, or even a vegan recipe delivery, there are many food delivery meal kits to push you to be more adventurous in the
                  kitchen. Naturally, not everyone has the time to plan, prepare and cook their meals from scratch, so finding the best home meal kits can really help you to become a culinary genius in the kitchen with minimal effort.
                </p>
                <div class="content-box" v-for="i in 5" :key="`box${i}`">
                  <h4>mini title</h4>
                  <p>content</p>
                </div>
              </div>
           </div>
      </div>
    </div>
    </div>
    </div>
 </div>
</template>

<script>
import mainBaner from '../components/mainBaner' 
import filterComp from '../components/filtersComp' 
import productsComp from '../components/productsComp' 

export default {
    name:'index',
    components:{
      mainBaner,
      filterComp,
      productsComp
    }
}
</script>

<style lang="scss">
@import '../styles/variables.scss';
@import '../styles/bootstrap.scss'; 

 .index-page{  
   h5{
     font-size: 1rem;
   }
  .inner-layout{ 
    display: flex;
    flex-wrap: wrap;
    .main-content{
      flex:  0 0 66.6%;
    }
    .more-contnet-container{
      flex: 0 0 33.3%;
      .more-contnet{
        margin-left: 30px;
      }
      .articles{
          background: #f6f6f6;
          padding: 15px;
          .article-box{
            margin-bottom: 20px;
            display: flex;
            
              .image{   
                  width: 90px;
                  height: 90px;
                  background:$symantic-block-color;
            }
          }
        }
    }
  }
}
@include media-breakpoint-down(md) { 
  .index-page{  
      .inner-layout{ 
         .main-content{
      flex:  0 0 100%;
    }
    .more-contnet-container{
      flex: 0 0 100%;
     
       .more-contnet{
        margin-left: 0px;
      }
    }
    }
  }
 }
</style>

  
  