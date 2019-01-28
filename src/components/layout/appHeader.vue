<template>
    <header class="app-header">
      <div class="container">
        <div class="row">
          <div class="col-12">
        <div class="app-header-wrap">
             <div class="logo-wrap">
               <router-link class="logo" to="/">
               LOGO
              </router-link>
             </div>
              <nav class="menu">
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
        </div>
        </div>
      </div>
    </header>
</template>

<script>
export default {
  name: 'app-header',
 
};
</script>
<style lang="scss">
.app-header{
  .app-header-wrap{
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-between;
    .logo-wrap{
      flex: 0 0 30%;
    }
    .menu{
       flex: 0 0 70%;
       
      .items{  
        display: flex;
        justify-content: flex-end;
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
}

</style>

