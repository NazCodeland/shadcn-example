<script lang="ts">
	import GroupUsers from '$lib/components/group-users.svelte';
	import * as Menubar from '$lib/components/ui/menubar/index.js';
	import Checkbox from '$lib/components/ui/checkbox/checkbox.svelte';
	import Label from '$lib/components/ui/label/label.svelte';

	let { groups } = $props();
</script>

{#each groups as group (group)}
	<Menubar.Sub>
		<Menubar.SubTrigger class="p-0">
			<Label class="flex w-full items-center gap-2 p-2">
				<Checkbox class="pointer-events-none" />
				{group.title}
			</Label>
		</Menubar.SubTrigger>
		<GroupUsers groupUsers={group.users} />
	</Menubar.Sub>
{/each}
