<template>
  <div class="about">
    <h1>Hello,there!</h1>
    <iframe  src="https://www.youtube.com/embed/KTFH4P8unUQ?si=_DtoH28EoM5GDjuW"
      title="YouTube video player" frameborder="0"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
      referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
      <div>
        本網頁是練習VUE的簡單作品，原作者如上影片。基本上就是用預設的VUE範本修改而來，主要是用子元素的input用emit將代辦清單的字串丟到父層接收，父層收到更新ref的資料，用props方式迴圈將代辦事宜的框框秀出來，細部的邏輯控制就簡單的v-if、v-show、v-model等。至於編輯、修改狀態、刪除也都是相同的做法，emit自定義事件修改父層的元素後re-render一併改變展示的內容，跟簡單的路由控制。全部完成後有再做簡單的css修改跟中文化。That's it.
      </div>
  </div>
</template>

<style>
.about{
  line-height: 2rem;
}



@media (min-width: 1024px) {
  .about {
    padding-left: 200px;
    padding-right: 200px;
    padding-top: 2rem;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: start;
    flex-direction: column;
    gap:2rem;
  }

  iframe{
    width:560px; 
    height:315px;
  }
 
}

@media (max-width:600px) {
    iframe{
      width: 100vw;
      height: 315px;
    }
  }
</style>
