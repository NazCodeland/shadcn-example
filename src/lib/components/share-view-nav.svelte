<script lang="ts">
	import Groups from '$lib/components/groups.svelte';
	import * as Menubar from '$lib/components/ui/menubar/index.js';
	import * as Popover from '$lib/components/ui/popover/index.js';
	import { Button } from '$lib/components/ui/button/index.js';
	import ChevronsUpDown from '@lucide/svelte/icons/chevrons-up-down';
	import * as Command from '$lib/components/ui/command/index.js';
	import Check from '@lucide/svelte/icons/check';

	let value = $state('');
	const groupsWithUsers = [
		{
			title: 'Tech Innovators',
			users: [
				'@techguru',
				'@codingqueen',
				'@designwizard',
				'@gamemaster',
				'@webdevking',
				'@aiwhiz',
				'@frontendpro',
				'@backendboss',
				'@datadreamer'
			]
		},
		{
			title: 'Adventure Seekers',
			users: [
				'@techguru',
				'@codingqueen',
				'@designwizard',
				'@gamemaster',
				'@webdevking',
				'@aiwhiz',
				'@frontendpro',
				'@backendboss',
				'@datadreamer'
			]
		},
		{
			title: 'Gaming Legends',
			users: [
				'@techguru',
				'@codingqueen',
				'@designwizard',
				'@gamemaster',
				'@webdevking',
				'@aiwhiz',
				'@frontendpro',
				'@backendboss',
				'@datadreamer'
			]
		},
		{
			title: 'Design Masters',
			users: [
				'@techguru',
				'@codingqueen',
				'@designwizard',
				'@gamemaster',
				'@webdevking',
				'@aiwhiz',
				'@frontendpro',
				'@backendboss',
				'@datadreamer'
			]
		},
		{
			title: 'Coders United',
			users: [
				'@techguru',
				'@codingqueen',
				'@designwizard',
				'@gamemaster',
				'@webdevking',
				'@aiwhiz',
				'@frontendpro',
				'@backendboss',
				'@datadreamer'
			]
		},
		{
			title: 'AI Enthusiasts',
			users: [
				'@techguru',
				'@codingqueen',
				'@designwizard',
				'@gamemaster',
				'@webdevking',
				'@aiwhiz',
				'@frontendpro',
				'@backendboss',
				'@datadreamer'
			]
		},
		{
			title: 'Frontend Wizards',
			users: [
				'@techguru',
				'@codingqueen',
				'@designwizard',
				'@gamemaster',
				'@webdevking',
				'@aiwhiz',
				'@frontendpro',
				'@backendboss',
				'@datadreamer'
			]
		},
		{
			title: 'Backend Builders',
			users: [
				'@techguru',
				'@codingqueen',
				'@designwizard',
				'@gamemaster',
				'@webdevking',
				'@aiwhiz',
				'@frontendpro',
				'@backendboss',
				'@datadreamer'
			]
		},
		{
			title: 'Data Dreamers',
			users: [
				'@techguru',
				'@codingqueen',
				'@designwizard',
				'@gamemaster',
				'@webdevking',
				'@aiwhiz',
				'@frontendpro',
				'@backendboss',
				'@datadreamer'
			]
		},
		{
			title: 'Creative Thinkers',
			users: [
				'@techguru',
				'@codingqueen',
				'@designwizard',
				'@gamemaster',
				'@webdevking',
				'@aiwhiz',
				'@frontendpro',
				'@backendboss',
				'@datadreamer'
			]
		}
	];
</script>

<Menubar.Root>
	<Menubar.Menu>
		<Menubar.Trigger>Click Me</Menubar.Trigger>

		<Menubar.Content>
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
								{#each groupsWithUsers as group (group.title)}
									<Command.Item
										value={group.title}
										onSelect={() => {
											value = group.title;
										}}
									>
										<Check />
										{group.title}
									</Command.Item>
								{/each}
							</Command.Group>
						</Command.List>
					</Command.Root>
				</Popover.Content>
			</Popover.Root>

			<Groups groups={groupsWithUsers} />
		</Menubar.Content>
	</Menubar.Menu>
</Menubar.Root>
