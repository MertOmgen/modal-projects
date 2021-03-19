<template>
  <form>
      <label>Email:</label>
      <input type="email" required v-model="email">

      <label>Password:</label>
      <input type="password" required v-model="password">

      <label>Role:</label>
      <select v-model="role" >
          <option value="default">Default</option>
          <option value="dev">Developer</option>
          <option value="designer">Designer</option>
      </select>

<div>
    <input type="checkbox" v-model="terms" required>
    <label>Terms</label>
</div>
<div>
    <input type="checkbox" value="Mert" v-model="names">
    <label>Mert</label>
    <input type="checkbox" value="Salih" v-model="names">
    <label>Salih</label>
    <input type="checkbox" value="Serkan" v-model="names">
    <label>Serkan</label>
</div>
  </form>

  <p>
      E-mail : {{email}}
  </p>

  <p>    Password : {{password}}</p>
  <p>    Role : {{role}}</p>
  <p>Terms : {{terms}}</p>
  <p>Names : {{names}}</p>
</template>
<script>

/* v-model => Bize 2-way data binding işlemini yapmamızı sağlayan propertydir. Yani data propertylerimizi ilgili input içerisinde girilen
veri ile doldurmak istediğimizde ilgili inputa v-model="email" veriririz. Böylelikle input içerisinde girilen değeri e-mail propertysinde
tutarız.
Aynı zamanda email data propertysine başlangıçta bir değer atadığımızda bu değerin de input içerisinde gösterilmesini sağlarız.

<!-- Eğer Birden fazla checkbox kullanacaksak data propertysi olarak boş bir array tanımlarız ve o array içerisine checkboxların 
value değerlerini basarız.
 -->

 */


export default {
data(){
    return{
        email:'mertomgen@gmail.com',
        password:'',
        role:'default',
        terms:false,
        names:[]

    }
}
}
</script>

<style>

</style>