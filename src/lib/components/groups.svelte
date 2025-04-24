<script lang="ts">
	import GroupUsers from '$lib/components/group-users.svelte';
	import * as Menubar from '$lib/components/ui/menubar/index.js';

	let { groups } = $props();
</script>

{#each groups as group (group)}
	<Menubar.Sub>
		<Menubar.SubTrigger>{group.title}</Menubar.SubTrigger>
		<GroupUsers groupUsers={group.users} />
	</Menubar.Sub>
{/each}
