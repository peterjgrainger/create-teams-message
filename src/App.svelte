<script>
	export let gitHubOrg = 'your-org';
	export let gitlabGroupName = 'gitlab group';
	export let timezone = 'timezone e.g. CET';
	export let migrationDate = 'migration date e.g. 5th April 2022';
	export let owner = 'owner of the GitLab project';
	export let gitlabUrl = 'https://gitlab.com'
	export let listOfRepos = 'repo1\nrepo2\nrepo3';

	$: if(listOfRepos) {
		console.log('changed');
	}
</script>

<main>
	<h1>Create a message when migrating from GitLab to GitHub</h1>
	<input type="text" bind:value={owner} /><br/>
	<input type="text" bind:value={gitHubOrg} /><br/>
	<textarea rows=10 bind:value={listOfRepos}></textarea><br/>
	<input type="text" bind:value={gitlabGroupName} /><br/>
	<input type="text" bind:value={timezone} /><br/>
	<input type="text" bind:value={migrationDate}/><br/>
	<input type="text" bind:value={gitlabUrl}/><br/>

	<p># Migration of {gitlabGroupName} from GitLab to GitHub on {migrationDate}</p>
	<p>Owner: {owner}</p>
	<p>Date of transfer: {migrationDate}</p>
	<p>Timezone: {timezone}</p>
	<p>All GitLab users in a team in GitHub: TODO </p>

Migrations:
<ul>
	{#each listOfRepos.split('\n') as repo}
		<li> {gitlabUrl}/{gitlabGroupName}/{repo} -> https://github.com/{gitHubOrg}/{gitlabGroupName.toLowerCase()}-{repo.toLowerCase()} </li>
	{/each}
</ul>
	</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	input {
		width: 100%;
	}

	textarea {
		width: 100%;
		height: 100%;
		rows: 10
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>