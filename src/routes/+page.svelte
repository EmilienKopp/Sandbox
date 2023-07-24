<script lang="ts">
    import { createClient } from '@supabase/supabase-js';
    import { PUBLIC_SUPABASE_ANON_KEY, PUBLIC_SUPABASE_URL } from '$env/static/public'

    const supabase = createClient(PUBLIC_SUPABASE_URL, PUBLIC_SUPABASE_ANON_KEY);

    let user: any;

    async function signInWithGoogle() {
        const {data, error} = await supabase.auth.signInWithOAuth({
            provider: 'google',
        })
        if (error) console.log(error)
        else {
            user = data;
            console.log(user)
        }
    }

</script>
<svelte:head>
    <title>Home</title>
</svelte:head>


<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>



<button on:click={signInWithGoogle} class="rounded-md bg-blue-400 text-white p-2">Sign in with Google</button>

{#if user}
  {user}
{/if}