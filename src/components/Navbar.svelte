<script lang="ts">
    import Router, {location, link} from 'svelte-spa-router';
    import Home from "../routes/Home.svelte";
    import Projects from "../routes/Projects.svelte";
</script>

<div class="navbar shadow-md bg-[#1A1A1A] text-white">
  <div class="flex-1">
    <p class="ml-2 text-xl">Queaxtra</p>
  </div>
  <div class="flex-none">
    <ul class="menu menu-horizontal">
        <li><a href="/" class="hover:bg-[#141414] hover:rounded"><i class="fa-solid fa-house"></i> Home</a></li>
        <li><a href="/#/projects" class="hover:bg-[#141414] hover:rounded"><i class="fa-solid fa-compass"></i> Projects</a></li>
    </ul>
  </div>
</div>

<Router routes={{
    '/': Home,
    '/projects': Projects,
}} />