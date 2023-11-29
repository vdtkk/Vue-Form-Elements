<template>
  <div class="container">
    <h3>Form Verileriyle Çalışmak</h3>
    <hr>
    <div class="row">
      <div class="col-md-6">
        <div class="panel panel-warning">
          <div class="panel-heading">
            <h4>Başvuru Formu</h4>
          </div>
          <div class="panel-body">
            <form>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label for="email">Kullanıcı Adı</label>
                    <input  type="text" 
                    id="username" 
                    class="form-control" 
                      :value="userData.userName"  
                      @input="userData.userName= $evet.target.value"
                      
                      
                      >
                  </div>
                  <div class="form-group">
                    <label for="password">Şifre</label>
                    <input type="password" 
                    id="password" 
                    class="form-control" 
                    v-model.lazy="userData.password">
                  </div>
                  <div class="form-group">
                    <label for="age">Yaş</label>
                    <input type="number" 
                    id="age" 
                    class="form-control" 
                    v-model="userData.age">
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label for="message">Açıklama</label><br>
                  <textarea id="message" rows="3" class="form-control" v-model="userData.message"></textarea>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label>
                      <input v-model="userData.interests" type="checkbox" value="yazilim"> Yazılım
                    </label>
                    <label>
                      <input v-model="userData.interests" type="checkbox" value="donanim"> Donanım
                    </label>
                  </div>

                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label>
                    <input v-model="userData.gender" type="radio" value="ERKEK"> Erkek
                  </label>
                  <label>
                    <input v-model="userData.gender" type="radio" value="KADIN"> Kadın
                  </label>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 from-group">
                  <label>Şehir</label>
                  <select v-model="userData.selectedCity" class="form-control">
                    <option :selected="city=='Adana'"
                    v-for="city in userData.cities"> {{ city }} </option>
                  </select>
                </div>
              </div>
              <hr>
              <div class="row">
                <div class="col-md-12">
                  <button @click.prevent="submit"
                    class="btn btn-primary">Gönder!
                  </button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
      <div class="col-md-6" v-if="isSubmitted">
          <div class="panel panel-info">
            <div class="panel-heading">
              <h4>Form Verileri</h4>
            </div>
            <div class="panel-body">
              <p>Kullanıcı Adı: {{ userData.userName }}</p>
              <p>Şifre: {{ userData.password }}</p>
              <p>Yaş: {{ userData.age }}</p>
              <p style="white-space: pre;">Açıklama:{{ userData.message }}</p>
              <p><strong>İlgi Alanları</strong></p>
              <ul>
                <li v-for="item in userData.interests"> {{item}}</li>
              </ul>
              <p>Cinsiyet: {{  userData.gender }}</p>
              <p>Şehir:{{ userData.selectedCity }}</p>
              <p>Toggle:</p>
            </div>
          </div>
      </div>
    </div>

  </div>
</template>

<script>
  export default {
  
    data(){

    return{
      userData:{
        userName:'',
        password:'',
        age:30, 
        message:'',
        interests:[],
        gender:'',
        cities:["istanbul","Ankara","Adana","Çankırı","Konya"],
        selectedCity:'',
        isSubmitted:false
      },
   }
      },
      methods:{

        submit (){

          this.isSubmitted=True;


        }

      }
  
  }
</script>

<style>

</style>
