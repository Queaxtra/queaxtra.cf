<script lang="ts">
	import { useLanyard } from 'svelte-lanyard';
	const data = useLanyard('825370766999552011');
    const date = new Date();
    const year = date.getFullYear();
    const age = year - 2005;
</script>

{#if $data}
<center>
    <div class="w-40 h-40 bg-[#1A1A1A] rounded mt-32 md:mt-40 shadow-md border-b-4 border-[#0c0c0c]">
        <img class="rounded-full relative top-3.5" src="https://cdn.discordapp.com/avatars/{$data.discord_user.id}/{$data.discord_user.avatar}.png">
        {#if $data.discord_status === "dnd"}
        <div class="tooltip w-4 h-4 bg-red-500 relative mt-2 ml-32 rounded-full drop-shadow-md" data-tip="Do not Disturb"></div>
        {/if}
        {#if $data.discord_status === "online"}
        <div class="tooltip w-4 h-4 bg-green-500 relative mt-2 ml-32 rounded-full drop-shadow-md" data-tip="Online"></div>
        {/if}
        {#if $data.discord_status === "idle"}
        <div class="tooltip w-4 h-4 bg-yellow-500 relative mt-2 ml-32 rounded-full drop-shadow-md" data-tip="Idle"></div>
        {/if}
        {#if $data.discord_status === "offline"}
        <div class="tooltip w-4 h-4 bg-gray-500 relative mt-2 ml-32 rounded-full drop-shadow-md" data-tip="Offline"></div>
        {/if}
    </div>
    <div>
        <h2 class="text-white text-2xl mt-5">{$data.discord_user.username}<span class="opacity-50 text-xl">#{$data.discord_user.discriminator}</span></h2>
        <p class="mt-2 text-gray-500">{age} years old, Front-end Developer</p>
        {#if $data.listening_to_spotify === true}
        <div class="mt-2">
            <p class="text-gray-500"><i class="fa-brands fa-spotify"></i> Listening on <a href="https://open.spotify.com/track/{$data.spotify.track_id}" class="text-white">{$data.spotify.song}</a></p>
        </div>
        {/if}
        {#if $data.listening_to_spotify === false}
        <div class="mt-2">
            <p class="text-gray-500"><i class="fa-brands fa-spotify"></i> Nothing is listening!</p>
        </div>
        {/if}
        <div class="h-14 w-64 bg-[#1A1A1A] rounded mt-3 shadow-md border-b-4 border-[#0c0c0c]">
            <div class="tooltip w-10 h-10 bg-[#141414] rounded relative top-1.5" data-tip="Instagram">
                <a href="https://instagram.com/queaxtra"><i class="fa-brands fa-instagram text-xl text-white mt-1.5"></i></a>
            </div>
            <div class="tooltip w-10 h-10 bg-[#141414] rounded relative top-1.5" data-tip="Github">
                <a href="https://github.com/Queaxtra"><i class="fa-brands fa-github text-xl text-white mt-1.5"></i></a>
            </div>
            <div class="tooltip w-10 h-10 bg-[#141414] rounded relative top-1.5" data-tip="Twitter">
                <a href="https://twitter.com/Queaxtra"><i class="fa-brands fa-twitter text-xl text-white mt-1.5"></i></a>
            </div>
            <div class="tooltip w-10 h-10 bg-[#141414] rounded relative top-1.5" data-tip="Discord">
                <a href="https://discord.com/users/825370766999552011"><i class="fa-brands fa-discord text-xl text-white mt-1.5"></i></a>
            </div>
        </div>
    </div>
</center>
{:else}
<center>
  <h2 class="text-2xl mt-44 text-white md:mt-96">A connection is being established with the website...</h2>
</center>
{/if}