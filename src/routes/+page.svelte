<script lang="ts">
	import { Accordion } from 'bits-ui';
	import { Pagination } from 'bits-ui';

	import * as ShadcnSvelteAccordion from '$lib/components/ui/accordion';
	import * as ShadcnSveltePagination from '$lib/components/ui/pagination';
</script>

<h1 class="border-t-8 border-teal-500">Bit UI Accordion with Render Delegation - works</h1>
<br />

<Accordion.Root>
	<Accordion.Item value="first">
		<Accordion.Header>
			<Accordion.Trigger asChild let:builder>
				<div use:builder.action {...builder}>Open accordion item</div>
			</Accordion.Trigger>
		</Accordion.Header>
		<Accordion.Content>First accordion content</Accordion.Content>
	</Accordion.Item>
</Accordion.Root>

<br /><br />

<h1 class="border-t-8 border-teal-500">Shadcn-Svelte Accordion with Render Delegation - works</h1>
<br />

<ShadcnSvelteAccordion.Root>
	<ShadcnSvelteAccordion.Item value="item-1">
		<Accordion.Trigger asChild let:builder>
			<div use:builder.action {...builder}>Open accordion item</div>
		</Accordion.Trigger>
		<ShadcnSvelteAccordion.Content
			>Yes. It adheres to the WAI-ARIA design pattern.</ShadcnSvelteAccordion.Content
		>
	</ShadcnSvelteAccordion.Item>
</ShadcnSvelteAccordion.Root>

<br /><br />

<h1 class="border-t-8 border-teal-500">
	Bit UI <strong>Pagination</strong> with Render Delegation - works
</h1>
<br />

<Pagination.Root count={100} perPage={10} let:pages>
	<Pagination.PrevButton asChild let:builder>
		<div use:builder.action {...builder}>Previous</div>
	</Pagination.PrevButton>
	{#each pages as page (page.key)}
		<Pagination.Page {page} />
	{/each}
	<!-- <Pagination.NextButton /> -->
	<Pagination.NextButton asChild let:builder>
		<div use:builder.action {...builder}>Next</div>
	</Pagination.NextButton>
</Pagination.Root>

<br /><br />

<h1 class="border-t-8 border-teal-500">
	Shadcn-Svelte <strong>Pagination</strong> with Render Delegation - error
</h1>
<br />

<ShadcnSveltePagination.Root count={100} perPage={10} let:pages let:currentPage>
	<ShadcnSveltePagination.Content>
		<ShadcnSveltePagination.Item>
			<!-- <ShadcnSveltePagination.PrevButton /> -->

			<!-- ERROR - Property 'builder' does not exist on type '{}' -->
			<ShadcnSveltePagination.PrevButton asChild={true} let:builder>
				<div use:builder.action {...builder}>Previous</div>
			</ShadcnSveltePagination.PrevButton>
			<!--  -->
		</ShadcnSveltePagination.Item>
		{#each pages as page (page.key)}
			{#if page.type === 'ellipsis'}
				<ShadcnSveltePagination.Item>
					<ShadcnSveltePagination.Ellipsis />
				</ShadcnSveltePagination.Item>
			{:else}
				<ShadcnSveltePagination.Item>
					<ShadcnSveltePagination.Link {page} isActive={currentPage == page.value}>
						{page.value}
					</ShadcnSveltePagination.Link>
				</ShadcnSveltePagination.Item>
			{/if}
		{/each}
		<ShadcnSveltePagination.Item>
			<ShadcnSveltePagination.NextButton />
		</ShadcnSveltePagination.Item>
	</ShadcnSveltePagination.Content>
</ShadcnSveltePagination.Root>
