<script>
  let { navigate } = $props();
  
  const biodata = {
    nama: "Muhammad Irfan Edrian",
    nim: "12450112580",
    wa: "081259291679",
    email: "muhammadirfanedrian@gmail.com"
  };
</script>

<div style="background: #121212; padding: 30px; border-radius: 20px; text-align: center; max-width: 400px; margin: 20px auto; border: 2px solid #333; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; color: white;">
  
  <div style="margin-bottom: 20px;">
    <img 
      src="/foto-irfan.jpeg" 
      alt="Profil Irfan" 
      style="width: 140px; height: 140px; border-radius: 50%; object-fit: cover; border: 4px solid #ff3e00; box-shadow: 0 0 20px rgba(255, 62, 0, 0.2);"
    />
  </div>

  <h2 style="margin: 10px 0 5px; color: #fff; letter-spacing: 1px;">{biodata.nama}</h2>
  <p style="color: #ff3e00; font-weight: bold; margin-bottom: 25px; font-size: 0.9rem; text-transform: uppercase;">Informatics Engineering</p>

  <div style="text-align: left; background: #1e1e1e; padding: 20px; border-radius: 12px; border: 1px solid #333; line-height: 2;">
    <div style="display: flex; justify-content: space-between; border-bottom: 1px solid #333; padding-bottom: 5px; margin-bottom: 10px;">
      <span style="color: #888;">NIM</span>
      <span style="color: #fff;">{biodata.nim}</span>
    </div>
    <div style="display: flex; justify-content: space-between; border-bottom: 1px solid #333; padding-bottom: 5px; margin-bottom: 10px;">
      <span style="color: #888;">WhatsApp</span>
      <span style="color: #fff;">{biodata.wa}</span>
    </div>
    <div style="display: flex; flex-direction: column;">
      <span style="color: #888;">Email</span>
      <span style="color: #ff3e00; font-size: 0.85rem;">{biodata.email}</span>
    </div>
  </div>

  <button 
    onclick={() => navigate('/')} 
    style="margin-top: 25px; width: 100%; padding: 12px; border: none; border-radius: 8px; background: #ff3e00; color: white; font-weight: bold; cursor: pointer; transition: 0.3s;"
  >
    KEMBALI KE JADWAL
  </button>

</div>

<style>
  /* Tambahan biar background seluruh halaman ikut gelap saat di profil */
  :global(body) {
    background-color: #000 !important;
    transition: background 0.5s;
  }
</style>