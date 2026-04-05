<script>
  import Home from "./pages/Home.svelte";
  import Detail from "./pages/Detail.svelte";
  import Profile from "./pages/Profile.svelte"; // Pastikan baris ini ADA

  let currentPath = $state(window.location.pathname);
  let selectedId = $state(null);

  function navigate(path, id = null) {
    window.history.pushState({}, "", path);
    currentPath = path;
    selectedId = id;
  }

  window.onpopstate = () => {
    currentPath = window.location.pathname;
  };
</script>

<nav style="background: #ff3e00; padding: 15px; color: white; text-align: center; font-weight: bold;">
  PORTAL PKU - IRFAN
</nav>

<main style="padding: 15px; padding-bottom: 80px;">
  {#if currentPath === "/" || currentPath === "/index.html"}
    <Home {navigate} />
  {:else if currentPath === "/profile"}
    <Profile {navigate} />
  {:else if currentPath.includes("/detail")}
    <Detail id={selectedId || currentPath.split('/').pop()} {navigate} />
  {/if}
</main>

<div style="position: fixed; bottom: 0; width: 100%; background: white; display: flex; justify-content: space-around; padding: 15px 0; border-top: 1px solid #ddd;">
  <button onclick={() => navigate('/')} style="background: none; border: none; cursor: pointer;">
    {currentPath === '/' ? '🕌 **Jadwal**' : '🕌 Jadwal'}
  </button>
  <button onclick={() => navigate('/profile')} style="background: none; border: none; cursor: pointer;">
    {currentPath === '/profile' ? '👤 **Profil**' : '👤 Profil'}
  </button>
</div>