<template>
  <section class="my-1">
    <modal v-if="modalVideo">
          <iframe :src="`${video.video}`" frameborder="0"></iframe>
    </modal>
        <div class="container">
          <div class="my-2 ruta">
            <router-link to="/" > Inicio </router-link> /
            <span> {{video.title}}</span>
          </div>
           <article class="video flex">
                <div class="video__poster">
                  <img :src="video.img" alt="">
                </div>
                <div class="video__caption">
                   <h2 class="video__title">{{video.title}}</h2>
                   <p class="mb-1">{{video.categoria}}</p>
                   <p class="mb-1">{{video.Descricpcion}}</p>
                 <button class="btn mr-1" @click="modalOpen" >Ver Trailer</button>
                  <button class="btn btn-line">Compartir</button>
                </div>
           </article>
        </div>
    </section>
</template>

<script>
import modal from '@/components/modal'

export default {
  name:'video',
  components: {
    modal
  },
  data(){
    return{
      modalVideo: false,
      video:{}
    }
  },
  methods: {
    async getVideo(){
      const info = await fetch(`http://localhost:3000/video/${this.$route.params.id}`),
            data = await info.json()
      this.video = data
      console.log(data)
    },
    modalOpen(){
    this.modalVideo = !this.modalVideo
    }
  },
  
  created(){
    this.getVideo();
  }

}
</script>


<style lang="scss">
/*colores*/
$color-principal: #2593fa;
$color-secundary: #198fd4;
$color-third:#fff;
 
$color-auxiliar:#067fcf;
$color-auxiliar-secundary:rgb(64, 160, 207);

/*font-weight*/

$font-bold:600;
$font-normal:400;
$font-light:300;

/*font-size*/
$font-size-small:14px;
$font-size:16px;
$font-size-large:22px;
$font-size-xlarge:36px;

/*font-family*/
$font-roboto: Arial, Helvetica, sans-serif ;
$font-helvetica: Helvetica, Arial, sans-serif;

//mixins
@mixin mediaQ($breakpoint) {
    @media screen and (min-width: $breakpoint){
      @content;
    }
  }
  *, 
*::after,
*::before{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

ul{
    list-style: none;
}
a{
    text-decoration: none;
}
.text-center{
    text-align: center;
}
body{
    font-family: $font-roboto;
    background-color: #fff;
}
.img-responsive{
    max-width: 100%;
    display: block;
}
.material-icons{
    cursor: pointer;
}

.flex{
    display: flex;
    &.direction-column{
        flex-direction: column;
    }
    &.justify-between{
        justify-content: space-between;
    }
    &.justify-end{
        justify-content: flex-end;
    }
    &.justify-center{
        justify-content: center;
    }
    &.align-center{
        align-items: center;
    }
    &.wrap{
        flex-wrap: wrap;
    }
}
.grid{
    display: grid;
}



.mx-1{
    margin-left: 1em;
    margin-right: 1em;
}
.mx-2{
    margin-left: 2em;
    margin-right: 2em;
}

.my-m1{
    margin-top: .5em;
    margin-bottom: .5em;
}
.my-1{
    margin-top: 1em;
    margin-bottom: 1em;
}
.my-2{
    margin-top: 2em;
    margin-bottom: 2em;
}
.mb-1{
    margin-bottom: 1em;
}
.mb-2{
    margin-bottom: 2em;
}
.mr-1{
    margin-right: 1em;
}

.px-1{
    padding-left: 1em;
    padding-right: 1em;
}
.py-1{
    padding-top: 1em;
    padding-bottom: 1em;
}
.pb-1{
    padding-bottom: 1em;
}
.pb-2{
    padding-bottom: 2em;
}

.container{
    width: 100%;
    margin: 0 auto;
    padding-right: 15px;
    padding-left: 15px;

    @media (min-width: 1366px){
        width: 1200px;
    }
    @media (min-width: 1600px){
        width: 1500px;
    }
}
.btn{

    cursor: pointer;
    padding: .5em 1.2em;
    border: 1px solid $color-secundary;
    background-color:$color-secundary;
    color:#fff;
    border-radius: 4px;
    transition: background-color .4s, border .4s ;
    margin-bottom:.4em;
    &.btn-line{
        border: 1px solid $color-secundary;
        background-color: #fff;
        color:$color-secundary;
        transition: background-color .5s, color .5s, border .5s  ;
        &:hover{
            color:#fff;
        }
    }
    &:hover{
        background-color:$color-auxiliar;
        border: 1px solid $color-auxiliar;
    }
}
.video{
    padding: 1em ;
    background-color: rgb(252, 252, 252);
    margin: 0 auto;
    margin-bottom: 1.2em;
    border-radius:6px;
    box-shadow: 1px 1px 4px rgba(59, 59, 59, 0.363);
    width: 100%;
    &__caption{
      padding: .5em 1em;
      width: 70%;
    }
    &__title{
        margin :0;
        margin-bottom: .7em;
        color: $color-secundary;
    }
    &__poster{
        overflow: hidden;
        border-radius:6px;
        margin-bottom: 1em;
        img{
            max-height: 100%;
            display: block;
            margin: 0 auto;
        }
    }
    &__list{
        font-size:$font-size-small;
        margin-bottom: 1em;
    }
}
.ruta{
  font-size:$font-size-small;
  color: gray;
}

</style>

