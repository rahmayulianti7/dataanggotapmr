<template>
  <div>
    <h1>isi data anggota</h1>
    <form @submit.prevent="simpan">

    <input v-model="nama" > <br/>
    <input type="number" v-model="kelas" placeholder="kelas" ><br/>
    <button type="submit">kirim</button>
    <Nuxt-link to="/">kembali</Nuxt-link>
    </form>
   </div>
</template>

<script setup>
const supabase= useSupabaseAuthClient()

const nama= ref()
const kelas= ref()
const simpan = async ()=>{
  const {data,error} = await supabase
  .from("dataanggotapmr")
  .insert({
    nama:nama.value,
    kelas:kelas.value
  })
  alert("suskses menambahkan siswa  pmr")
  navigateTo("/")
  if(error){
  console.log(error)
  }
}
</script>

