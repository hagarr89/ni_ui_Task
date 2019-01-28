<template>
    <div class="app-footer">
        <div class="container">
        <div class="row">
          <div class="col-12">
        <div class="footer-layout">
              <div class="logo-wrap footer-left">
               <router-link class="logo" to="/">
               LOGO
              </router-link>
             </div>
              <nav class="menu footer-right">
                <ul class="items">
                  <li class="item">
                       <a href="javascript:;" class="link-item"> item link</a>
                    </li>
                     <li class="item">
                      <a href="javascript:;" class="link-item"> item link</a>
                    </li>
                     <li class="item">
                       <a href="javascript:;" class="link-item"> item link</a>
                    </li>
                </ul>
              </nav>
        </div>
            <div class="footer-layout bottom">
                    <div class="footer-left">
                        text
                    </div>
                    <div class="footer-right">
                        text
                    </div>
            </div>
          </div>
          </div>
        </div>
    </div>
</template>
<script>
export default {
  name: 'app-footer',
};
</script>
<style lang="scss">
.app-footer{
    min-height: 202px;
    background-color: #f7f7f7;
    display: flex;
    align-items: center;
    .footer-layout{
        display: flex;
        align-items: center;
        flex-wrap: wrap;
        &.bottom{
            margin-top: 35px;
            font-size: 0.85rem;

        }
    }
    .footer-right{
        text-align: center;
    }
    .footer-right{ flex: 0 0 57%; display: flex; align-items: center; justify-content:center; }
    .footer-left {flex: 0 0 43%; }
    .menu{       
      .items{  
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        .item{
            &:last-child{
              .link-item{
              padding-right: 0;
              }
            }
        }
        .link-item{
            padding-right: 10px;
            
        }
      }
    }
}
</style>

