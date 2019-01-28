<template>
    <div class="product-comp">
        <div class="top d-md-none">
                 <a href="javascript:;" class="logo">
                        <img src="../assets/logo-home-chef.png" alt="logo"/>
                </a>
                <div class="btn-wrap read">
                        <a href="javascript:;" class="read-btn">Read Review</a>
                </div>
        </div>
        <div class="image-wrap">
            <div class="image-inner-wrap">
                <div class="content">
                    <div class="image"></div>
                    <div class="play"></div>
                     <div class="score  d-md-none d-md-block">
                        <div class="inner-score">
                            <span class="total-score text">9.8</span>
                             <span class="text small">our score</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="content-wrap">
            <div class="inner-content">
                <div class="top d-none d-md-flex">
                    <a href="javascript:;" class="logo">
                        <img src="../assets/logo-home-chef.png" alt="logo"/>
                    </a>
                    <div class="score">
                        <div class="inner-score">
                               <span class="text small">our score</span>
                            <span class="total-score text">9.8</span>
                        </div>
                    </div>
                </div>
                <ul class="check-list">
                    <li class="item" v-for="item in product.checkList" :key="`item${item.id}`" 
                    :class="{'d-none d-md-block':item.id == 3 }">
                        <span class="item-txt">{{item.text}}</span>
                    </li>
                </ul>
                <div class="btns-wrap">
                    <div class="btn-wrap read d-none d-md-block">
                        <a href="javascript:;" class="read-btn">Read Review</a>
                    </div>
                    <div class="btn-wrap order">
                        <a href="javascript:;" class="btn">Order Now</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name:'product-comp',
    props:['product']
}
</script>
<style lang="scss">
@import '../styles/bootstrap.scss'; 
@import '../styles/variables.scss';
@import '../styles/share.scss';


.product-comp{
    display: flex;
    flex-wrap: wrap;
     border-radius: 3px;
    box-shadow: 0 5px 15px 0 rgba(0, 0, 0, 0.1);
    background-color: #ffffff;
    border: 1px solid #e2e2e2;
    margin-bottom: 30px;
    padding: 5px;
  .btns-wrap{
      display: flex;
      flex-wrap: wrap;
      align-items: center;
  }
   .btn-wrap{
            flex: 0 0 50%;
            &.read{
                    text-align: center;
                     color: $primary-color;
                     font-size: 0.875rem;
            }
        }
    .image-wrap ,.content-wrap{
        flex: 0 0 50%;
    }
    .check-list{
        font-size: 0.75rem;
        margin-top: 10px;
        line-height: 1;
        .item{
            margin-bottom: 8px;
            position: relative;
            padding-left: 16px;
            &:last-child{
                margin-bottom: 10px;
            }
            &:before{
                content: '\e900';
                font-family: 'icomoon' !important;
                 color: #ff6a56;
                 font-size: 0.6875rem;
                padding-right: 0;
                position: absolute;
                 left: 0;
            }
        }
    }
    .content-wrap{
        .inner-content{
            padding:5px 5px 5px 10px;
        }
    }
      .top{
                display: flex;
                align-items: center;
                flex-wrap: wrap;
                justify-content: space-between;
                .score{
                    flex: 0 1 20%;
                    .inner-score{
                        display: inline-block;
                        float:right;
                         text-align: center;
                    }
                    .text{
                        display: block;
                        font-size: 0.685rem;
                    }
                    .total-score{
                        font-size: 1.5rem;
                        font-weight: bold;
                        color: #000000;
                    }
                }
               
            }
     .logo{
        flex: 0 0 50%;
        img{
            max-width: 100%;
        }
    }
    .image-inner-wrap{
        position: relative;
        &:before {
            display: block;
            content: "";
            width: 100%;
            padding-top: 56.2%;

        }
        > .content {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
        }
        .image{
            position: absolute;
            top: 0;
            right: 0;
            width: 100%;
            height: 100%;
            background-size: cover;
            z-index: 1;
            background-image: url(../assets/product-home-chef.jpg);
        }
        .play{
            width: 60px;
            height: 60px;
            background-color: rgba(0, 0, 0, 0.4);
            position: absolute;
            top: 0;
            bottom: 0;
            right: 0;
            left: 0;
            margin: auto;
            z-index: 2;
            border-radius: 100%;
            &:before{
                content: '';
                 width: 0; 
                height: 0; 
                border-top: 12px solid transparent;
                border-bottom: 12px solid transparent;
                border-left: 12px solid #fff;
                display: block;
                position: absolute;
                top: 0;
                right: 0;
                left: 6px;
                margin: auto;
                bottom: 0;
            }
        }
    }
}
@include media-breakpoint-down(sm) { 
  .product-comp{
     margin-bottom: 15px;
     .play{
            width: 40px;
            height: 40px;
     }
      .top{
          width: 100%;
          padding: 8px 8px 13px;
          .logo{
            flex:  0 0 50%;
            img{
                width: 100%;
                max-width: 118px;
            }
          }
          .btn-wrap.read{
              text-align: right;
              flex: 0 1 auto;
          }
         
      }
  .btns-wrap{
      display: block;
     .btn{
           font-size: 0.875rem;
     } 
  }
     .content-wrap {
         .inner-content{
             padding: 13px 8px 8px;
            display: flex;
            justify-content: space-between;
            align-items: center;
         }
     }
      .image-wrap{
          overflow: hidden;
        .score{
          background: #fff;
          width: 70px;
          height: 70px;
          border-radius: 50%;
          position: absolute;
          bottom: -35px;
          left: 8px;
          z-index: 1;
        display: flex;    
        justify-content: center;
        text-align: center;
        line-height: 1;
        .inner-score{
             flex-direction: column;
             height: 35px;
             display: flex;
            justify-content: center;
        }
        .text{
            font-size: 0.5rem;
        }
        .total-score {
            display: block;
            font-size: 1rem;
        }
        
        }
      }
    .image-wrap,  .content-wrap{
        flex:0 0 100%;
        
    }
  }
 }
</style>