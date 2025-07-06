<script lang="ts">
	import { BarChart3, LayoutDashboard, Database, FileText, FileText as FileDescriptionIcon, FileText as FileWordIcon, Folder, HelpCircle, Circle as InnerShadowTopIcon, List, FileBarChart, Search, Settings, Users, Camera } from "@lucide/svelte";
	import NavDocuments from "./nav-documents.svelte";
	import NavMain from "./nav-main.svelte";
	import NavSecondary from "./nav-secondary.svelte";
	import NavUser from "./nav-user.svelte";
	import * as Sidebar from "$lib/components/ui/sidebar/index.js";
	import type { ComponentProps } from "svelte";

	const data = {
		user: {
			name: "shadcn",
			email: "m@example.com",
			avatar: "/avatars/shadcn.jpg",
		},
		navMain: [
			{
				title: "Dashboard",
				url: "#",
				icon: LayoutDashboard,
			},
			{
				title: "Lifecycle",
				url: "#",
				icon: List,
			},
			{
				title: "Analytics",
				url: "#",
				icon: BarChart3,
			},
			{
				title: "Projects",
				url: "#",
				icon: Folder,
			},
			{
				title: "Team",
				url: "#",
				icon: Users,
			},
		],
		navClouds: [
			{
				title: "Capture",
				icon: Camera,
				isActive: true,
				url: "#",
				items: [
					{
						title: "Active Proposals",
						url: "#",
					},
					{
						title: "Archived",
						url: "#",
					},
				],
			},
			{
				title: "Proposal",
				icon: FileDescriptionIcon,
				url: "#",
				items: [
					{
						title: "Active Proposals",
						url: "#",
					},
					{
						title: "Archived",
						url: "#",
					},
				],
			},
			{
				title: "Prompts",
				icon: FileText,
				url: "#",
				items: [
					{
						title: "Active Proposals",
						url: "#",
					},
					{
						title: "Archived",
						url: "#",
					},
				],
			},
		],
		navSecondary: [
			{
				title: "Settings",
				url: "#",
				icon: Settings,
			},
			{
				title: "Get Help",
				url: "#",
				icon: HelpCircle,
			},
			{
				title: "Search",
				url: "#",
				icon: Search,
			},
		],
		documents: [
			{
				name: "Data Library",
				url: "#",
				icon: Database,
			},
			{
				name: "Reports",
				url: "#",
				icon: FileBarChart,
			},
			{
				name: "Word Assistant",
				url: "#",
				icon: FileWordIcon,
			},
		],
	};

	let { ...restProps }: ComponentProps<typeof Sidebar.Root> = $props();
</script>

<Sidebar.Root collapsible="offcanvas" {...restProps}>
	<Sidebar.Header>
		<Sidebar.Menu>
			<Sidebar.MenuItem>
				<Sidebar.MenuButton class="data-[slot=sidebar-menu-button]:!p-1.5">
					{#snippet child({ props })}
						<a href="##" {...props}>
							<InnerShadowTopIcon class="!size-5" />
							<span class="text-base font-semibold">Acme Inc.</span>
						</a>
					{/snippet}
				</Sidebar.MenuButton>
			</Sidebar.MenuItem>
		</Sidebar.Menu>
	</Sidebar.Header>
	<Sidebar.Content>
		<NavMain items={data.navMain as Array<{ title: string; url: string; icon: any }>} />
		<NavDocuments items={data.documents as Array<{ name: string; url: string; icon: any }>} />
		<NavSecondary items={data.navSecondary as Array<{ title: string; url: string; icon: any }>} class="mt-auto" />
	</Sidebar.Content>
	<Sidebar.Footer>
		<NavUser user={data.user} />
	</Sidebar.Footer>
</Sidebar.Root>
