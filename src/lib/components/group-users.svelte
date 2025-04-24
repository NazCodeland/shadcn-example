<script lang="ts">
	import * as Menubar from '$lib/components/ui/menubar/index.js';
	import * as Popover from '$lib/components/ui/popover/index.js';
	import { Button } from '$lib/components/ui/button/index.js';
	import ChevronsUpDown from '@lucide/svelte/icons/chevrons-up-down';
	import * as Command from '$lib/components/ui/command/index.js';
	import Label from '$lib/components/ui/label/label.svelte';
	import Checkbox from '$lib/components/ui/checkbox/checkbox.svelte';
	import Check from '@lucide/svelte/icons/check';

	let { groupUsers } = $props();
	let value = $state('');
</script>

<Menubar.SubContent
	class="grid max-h-[calc(100svh-65px)] overflow-auto"
	collisionPadding={{
		top: 58.5,
		bottom: 8
	}}
	sideOffset={6}
	align="start"
>
	<Popover.Root>
		<Popover.Trigger>
			{#snippet child({ props })}
				<Button
					variant="outline"
					class="w-[200px] cursor-default justify-between"
					{...props}
					role="combobox"
				>
					Search...
					<ChevronsUpDown class="opacity-50" />
				</Button>
			{/snippet}
		</Popover.Trigger>

		<Popover.Content class="w-[200px] p-0">
			<Command.Root class="">
				<Command.Input placeholder="family, friends..." class="h-9" />
				<Command.List>
					<Command.Empty>No group found.</Command.Empty>
					<Command.Group>
						<!-- replace shareState with a derived state that contains all countries cities and provinces  -->
						{#each groupUsers as userName (userName)}
							<Command.Item
								value={userName}
								onSelect={() => {
									value = userName;
								}}
							>
								<Check />
								{userName}
							</Command.Item>
						{/each}
					</Command.Group>
				</Command.List>
			</Command.Root>
		</Popover.Content>
	</Popover.Root>

	{#each groupUsers as groupUser}
		<Label for={groupUser} class="hover:bg-gray-100">
			<Menubar.Item closeOnSelect={false} class="flex gap-2">
				<Checkbox
					class="pointer-events-none data-[state=checked]:border-primary/0"
					id={groupUser}
				/>

				<span class=" ">
					{groupUser}
				</span>
			</Menubar.Item>
		</Label>
	{/each}
</Menubar.SubContent>
