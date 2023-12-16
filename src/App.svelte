<script>
	import Header from './components/Header.svelte';
	import Footer from './components/Footer.svelte';
	import Tabs from './shared/Tabs.svelte';
	import CreatePollForm from "./components/CreatePollForm.svelte";
	import PollList from "./components/PollList.svelte";

	// tabs
	let items = ['Current Polls', 'Add New Poll'];
	let activeTab = items[0];

	const handleAddPoll = (e) => {
		activeTab = items[0]
	}


</script>


<Header />

<main>
	<Tabs {items} {activeTab} on:tabChanged={(e) => activeTab = e.detail}></Tabs>
	{#if activeTab === 'Current Polls'}
		<PollList />
	{:else if activeTab === 'Add New Poll'}
		<CreatePollForm on:addPoll={handleAddPoll} />
	{/if}
</main>

<Footer />

<style>
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style>
