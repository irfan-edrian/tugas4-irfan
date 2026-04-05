<script>
  let { id, navigate } = $props();
</script>

<button onclick={() => navigate('/')} style="cursor: pointer; padding: 8px 15px; border-radius: 5px; border: 1px solid #ddd; background: white;">
  ← Kembali
</button>

<div style="background: white; padding: 30px; border-radius: 15px; text-align: center; margin-top: 20px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  <h2 style="text-transform: uppercase; color: #ff3e00; margin-bottom: 15px;">{id} Pekanbaru</h2>
  <div style="font-size: 1.1rem; color: #555; line-height: 1.8;">
    <p>Mari menunaikan shalat <b>{id}</b> tepat waktu untuk keberkahan.</p>
    <p>Pastikan Anda bersiap 10 menit sebelum waktu di atas untuk persiapan berwudhu.</p>
  </div>
  <hr style="border: 0; border-top: 1px solid #eee; margin: 25px 0;">
  <p><small>Data ini disinkronisasi dengan jadwal resmi Kemenag RI</small></p>
</div>