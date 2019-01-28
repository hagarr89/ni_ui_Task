<template>
    <div class="filter-comp">
        <div class="filters-wrap">
            <ul class="filters">
                <li class="filter-item">
                    <a href="javascript:;" class="filter-link">filter</a>
                </li>
                <li class="filter-item">
                    <a href="javascript:;" class="filter-link">filter</a>
                </li>
                <li class="filter-item">
                    <a href="javascript:;" class="filter-link">filter</a>
                </li>
                <li class="filter-item">
                    <a href="javascript:;" class="filter-link">filter</a>
                </li>
                <li class="filter-item">
                    <a href="javascript:;" class="filter-link">filter</a>
                </li>
                <li class="filter-item">
                    <a href="javascript:;" class="filter-link">filter</a>
                </li>
            </ul>
        </div>
        <div class="advertising">Advertising Disclosure</div>
    </div>
</template>
<script>
export default {
    name:'filter-comp'
}
</script>
<style lang="scss">
@import '../styles/variables.scss';
@import '../styles/share.scss';
.filter-comp{
     font-size: 0.875rem;
     display: flex;
     flex-wrap: wrap;
     align-items: center;
     justify-content: space-between;
     padding: 15px 0;
  .filters{
          display: flex;
      .filter-item{
          margin-right: 15px;
         .filter-link{
    
        }
      }
  } 
  .advertising{font-size: 0.75rem} 
}
</style>

