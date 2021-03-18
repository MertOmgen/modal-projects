<template>
  <div class="hello" :class="{fb : theme === 'fb'}">
    <h1>{{ header }}</h1>
    <p>{{text}}</p>
    <button @click="closeModal">Lacivert</button>

    <slot>Default Content</slot> 
    <div class="actions">
      <slot name="links"></slot>
      </div>
  </div>
</template>

<script>
export default {
props:['header','text','theme'], /* <= Proplar tanımladığımız component için bize;
 - Yeniden kullanılabilirlik, esneklik, istediğimiz gibi özelleştirebilme ve verileri tek bir kaynaktan yönetebilme olanağı sağlar.
 - Tanımladığımız propsları kullanma zorunluluğumuz bulunmamakta. Componentin çağrıldığı yerde kullanılmayan props var ise undefined
 olarak gelir ve yapıyı etkilemezler.
 - Propsları aşağıdaki gibi data tipini vererekte tanımlayabiliriz.
*/

  name: 'HelloWorld',
  // props: {
  //   msg: String
  // }
  methods:{
    closeModal(){
      console.log("Kapatıyorum..")
      this.$emit('close') /* $emit => Custom eventlar yaratmak için kullanabileceğimiz bir js fonksiyonudur. Emit içerisinde isimlendirdiğimiz
      custom eventi ile child componentin bulunduğu parent componentdeki bir methodu tetikletebiliriz. 
      Ör:<HelloWorld @close="toggleModal" /> Hello world bizim child componentimiz, App parent componentimiz biz burada belirttiğimiz closemodal
      methodu ile this.$emit tetikliyoruz bu da parent component içerisinde bulunan @close değeri olarak atadığımız toggleModal fonksiyonun
      tetiklenmesini sağlamakta.
      */
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1{
  color: green;
}
p{
  color: blue;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.hello.fb{
  background-color: darkblue;
}
.hello{
  background-color: magenta;
}
</style>
