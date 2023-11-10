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

HELLO WORLD

{#if user}
  {user}
{/if}