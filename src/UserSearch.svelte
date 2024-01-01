<script>

    import User from './User.svelte';

    let usernameQuery = '';

    let user; 

    function handleSubmit(e){
        e.preventDefault();
            fetch(`https://api.github.com/users/${usernameQuery}`)
            .then(resp =>resp.json())
            .then(data => (user = data ));
        


    }
</script>

<style>

    .user-search {
        padding:20px;
        margin-bottom:50px;
        background: lightgray;
        display: block;
        margin: 0 auto;
        
        
        }

        h2{

            margin: 0 0 15px;
            text-align:center ;
        }

        form{
            display: block;
            width: 50%;
            margin: 0 auto;
        }

        #search-box {
            display: block !important;
            width: 40%;
            margin: 0 auto !important;
        }
        button{
            background-color: #0079FF;
        }
</style>

<div class ="user-search"> 
    <div id = "search-box">

        <h2>Search for users </h2>
        <form on:submit={handleSubmit}>
        <input type="text" bind:value={usernameQuery}>
        <button>Search</button>
    </form>
    
    {#if user}
        <User username = {user.login} avatar = {user.avatar_url} />
    {/if}
</div>


</div>