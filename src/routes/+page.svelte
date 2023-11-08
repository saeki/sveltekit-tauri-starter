<script lang="ts">
  import { isTauriAvailable } from "$lib";
  import { getTauriVersion } from "@tauri-apps/api/app";
  import { onMount } from "svelte";

  const baseUrl = import.meta.env.VITE_API_BASE_URL;

  let message: string;
  let tauriVersion: string;

  onMount(async () => {
    const url = "/api/hello";
    fetch(baseUrl ? new URL(url, baseUrl) : url)
      .then((res) => res.text())
      .then((res) => (message = res));

    if (isTauriAvailable()) {
      try {
        tauriVersion = await getTauriVersion();
      } catch (e) {
        console.error(e);
      }
    }
  });
</script>

<h1>Welcome to SvelteKit{isTauriAvailable() ? " + Tauri" : ""}.</h1>

{#if message}
  <p>{message}</p>
{/if}

{#if tauriVersion}
  <p>Tauri: {tauriVersion}</p>
{/if}
