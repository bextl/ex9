<script>
//    import { onMount } from 'svelte';
    import Header from './Header.svelte';
    import User from './User.svelte';
    import UserSearch from './UserSearch.svelte';
	 import {onMount} from "svelte";

	
    let users;
	onMount(() =>{
		getGithubUsers();
	});

	function getGithubUsers(){
		fetch("https://api.github.com/users")
		.then(resp =>resp.json())
		.then(data=>(users = data));
	}

    
</script>


<Header />

<main>

    <UserSearch />
   
</main>
