<script>
  import { onMount } from "svelte";
  let { navigate } = $props();
  
  let jadwal = $state(null);
  let loading = $state(true);

  // ID Pekanbaru di database Kemenag adalah 1301
  onMount(async () => {
    try {
      const tgl = new Date().toISOString().split('T')[0]; // Tanggal hari ini
      const res = await fetch(`https://api.myquran.com/v2/sholat/jadwal/1301/${tgl}`);
      const data = await res.json();
      jadwal = data.data.jadwal;
      loading = false;
    } catch (e) {
      console.error("Gagal ambil data", e);
    }
  });

  // Filter waktu shalat, abaikan field tanggal
  let sholatData = $derived(jadwal ? Object.entries(jadwal).filter(([w]) => w !== 'date' && w !== 'tanggal') : []);
</script>

<h1 style="text-align: center; color: #333;">Jadwal Shalat Hari Ini</h1>
<p style="text-align: center; color: #777;">{jadwal?.tanggal || ''}</p>

{#if loading}
  <p style="text-align: center; margin-top: 20px;">Menghubungkan ke API Kemenag...</p>
{:else}
  <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 15px;">
    {#each sholatData as [waktu, jam]}
      <div 
        style="background: white; padding: 20px; border-radius: 10px; border-left: 5px solid #ff3e00; box-shadow: 0 3px 6px rgba(0,0,0,0.1); cursor: pointer;"
        onclick={() => navigate(`/detail/${waktu}`, waktu)}
      >
        <b style="text-transform: capitalize; color: #333; font-size: 0.9rem;">{waktu}</b>
        <p style="margin: 8px 0 0; font-size: 1.5rem; color: #ff3e00; font-weight: bold;">{jam}</p>
      </div>
    {/each}
  </div>
  <p style="text-align: center; margin-top: 20px; font-size: 0.9rem; color: #888;">Klik waktu shalat untuk rincian</p>
{/if}