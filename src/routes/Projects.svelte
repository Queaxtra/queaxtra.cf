<script lang="ts">
	import { useLanyard } from 'svelte-lanyard';
	const data = useLanyard('825370766999552011');
    const date = new Date();
    const year = date.getFullYear();
    const age = year - 2005;
    const githubrepos = (async () => {
        const response = await fetch("https://api.github.com/users/Queaxtra/repos");
        return await response.json()
    })()
</script>

{#if $data}
<center>
    {#await githubrepos}
    <center>
        <h2 class="text-2xl mt-96">Projects are being fetched...</h2>
    </center>
    {:then data}
    {#each data as repo}
    <div class="relative top-20 stats rounded border-none w-80 lg:w-96 md:top-40 drop-shadow-md mx-1 my-1">
        <div class="stat bg-[#1A1A1A] border-b-4 border-orange-600 text-white">
            <a href="https://github.com/{repo.name}" class="stat-value mt-5 text-xl font-medium">{repo.name}</a>
            <p class="p-3 text-gray-500">
                <i class="fa-solid fa-star"></i> {repo.stargazers_count}
            </p>
            <p class="p-3 -mt-5 text-gray-500">
                <i class="fa-solid fa-bookmark"></i> {repo.language || "No language"}
            </p>
        </div>
    </div>
    {/each}
    {/await}
</center>
{:else}
<center>
  <h2 class="text-2xl mt-44 text-white md:mt-96">A connection is being established with the website...</h2>
</center>
{/if}