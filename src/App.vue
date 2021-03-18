<template>
<div>
<button @click="toggleModal" v-if="!showModal">Sarı</button>

</div>

<div v-if="showModal">
<!-- 
  Bir den fazla componenti tek bir yerde toplamak istediğimiz de öncelikle onu <script> tagleri içerisinde import ederiz.Ör:import HelloWorld from './components/HelloWorld.vue'
    Daha sonrasında import ettiğimiz componenti components propertysi altında ilgili alan için ekliyoruz.
    En son olarak import ederken isimlendirdiğimiz şekliyle componenti bir html tagi olarak template içerisinde çağırıyoruz.
    Burada bundan dolayı isimlendirmeyi yaparken dikkat etmek gerekli her zaman ilk harfin büyük olmasına özen gösterilmeli.
    küçük harf kullanılacaksa herhangi bir html tagine karşılık gelmemesine dikkat edilmeli.!
 -->

<HelloWorld :header="header" :text="text" theme="fb" @close="toggleModal" />

</div>

<!-- 
  Slots => Slot yapısı, tekrar tekrar kullanılan componentlerdeki complex yapıların kullanımını kolaylaştırmak için kullanılır.
  A componenti yarattığımız B component içerisinde verdiğimiz verilerin A component de belli bir yerde gösterilmesini istediğimizde
  <slot></slot> taglerini A componentimizde oluştururuz. Böylelikle B componenti içerisinde verdiğimiz değerler slot tagleri arasında gösterilir.
  A componenti C componentinde de cağrıldığında C componenti içerisinde yazılan template slot tagleri neredeyse  yine orada gösterilir.

  Named slots => A componenti içerisinde yarattığımız slotlara name propertysini atayarak ("<slot name='links></slot>') oluşturulur.
   B componenti içerisinde bu name sahip bir slot oluşturulduysa render edilir. ("<template v-slot:links></template>") B componenti içerisinde
   nerede yazıldığı önemli olmaksızın A componentinde nerede tanımlandıysa orada render edilir.

   Default Slot Content => Eğer A componenti içerisinde bir default slot (<slot></slot>) yarattığımızda ona bir değer atarsak 
   (<slot>component default</slot>) B componenti içerisinde A componentinin template içerisinde (named slots hariç) bir değer 
   bulunmazsa A componenti içerisindeki default slot içerisine yazılmış olan değer getirilir.


<HelloWorld>

  <template v-slot:links>
    <a href="#">Giris</a>
    <a href="#">Cikis</a>    ====> A Componenti
  </template>

  <h1>Default</h1>
  <h2>Value</h2>

</HelloWorld>

    <slot>Default Content</slot> 
    <div class="actions">       =====> B Componenti
      <slot name="links"></slot>
    </div>
 -->

<!-- 
  ref propertysine verdiğimiz değer ile ilgili componenti refere edebiliyoruz. Bu sayede de ilgili componenti istediğimiz gibi manipüle
  edebiliriz.Asagidaki handleClick() methodunda kullanımını görebiliyoruz.
 -->
<input type="text" ref="name">

<button @click="handleClick">Click it</button>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components:{HelloWorld},
data(){
  return{
    header:'Fenerbahçe',
    text: 'Alex de Souza',
    showModal:false
  }
},
methods:{
  handleClick(){
    console.log(this.$refs.name)
    this.$refs.name.classList.add('active')
    this.$refs.name.focus()
  },
  toggleModal(){
    console.log("Açıyorum..")
this.showModal = !this.showModal;
  }

}
}
</script>

<style>
/* 
CSS ler, Vue da hangi component sayfasında yazdığımız farketmezsin ilgili tagi nerede kullandıysak o tagi etkilerler.
Bunun önüne geçmek için yani yazdığımız tagin yalnızca yazıldığı yerde etkili olması için belli yöntemler vardır.

1.Yontem : "Scoped" Scoped propertysini ilgili compenent sayfasındaki style içerisine verdiğimiz de sadece ilgili component içerisindeki
yapılar bundan etkilenecektir. Bunu da "scoped" tagini kullandığımız componentin stylingleri DOM tarafında render edilirken bunlara
bir data attribute ekler ve bu data attribute değerlerini css selector olarak kullanır.
 */

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
