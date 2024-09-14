<a target="_blank" href="https://www.bits-ui.com/docs/getting-started">https://www.bits-ui.com/docs/getting-started</a>

```shell
pnpm install bits-ui
```

```svelte
<script lang="ts">
	import { Accordion } from 'bits-ui';
</script>

<Accordion.Root>
	<Accordion.Item value="first">
		<Accordion.Header>
			<Accordion.Trigger>First</Accordion.Trigger>
		</Accordion.Header>
		<Accordion.Content>First accordion content</Accordion.Content>
	</Accordion.Item>
	<Accordion.Item value="second">
		<Accordion.Header>
			<Accordion.Trigger>Second</Accordion.Trigger>
		</Accordion.Header>
		<Accordion.Content>Second accordion content</Accordion.Content>
	</Accordion.Item>
	<Accordion.Item value="third">
		<Accordion.Header>
			<Accordion.Trigger>Third</Accordion.Trigger>
		</Accordion.Header>
		<Accordion.Content>Third accordion content</Accordion.Content>
	</Accordion.Item>
</Accordion.Root>
```

With Render Delegation

Error

```svelte
<script lang="ts">
	import { Accordion } from 'bits-ui';
</script>

<Accordion.Root>
	<Accordion.Item value="first">
		<Accordion.Header>
			<AccordionTrigger asChild let:builder>
				<div use:builder.action {...builder}>Open accordion item</div>
			</AccordionTrigger>
		</Accordion.Header>
		<Accordion.Content>First accordion content</Accordion.Content>
	</Accordion.Item>
</Accordion.Root>
```

Instead of **`AccordionTrigger`** it is **`Accordion.Trigger`** ! :skull:

Correct

```svelte
<script lang="ts">
	import { Accordion } from 'bits-ui';
</script>

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
```

Shadcn-Svelte

```
pnpm dlx svelte-add@latest tailwindcss
```

```shell
Packages: +5
+++++
Progress: resolved 5, reused 0, downloaded 5, added 5, done
svelte-add version 2.7.3

┌  Welcome to Svelte Add!
│
◇  Preconditions not met ────────────────────────────╮
│                                                    │
│  - clean working directory (Found modified files)  │
│                                                    │
├────────────────────────────────────────────────────╯
│
◇  Preconditions failed. Do you wish to continue?
│  Yes
│
◇  Do you want to use typography plugin?
│  Yes
│
◇  Successfully installed dependencies
│
◇  Successfully formatted modified files
│
└  You're all set!
```

```shell
pnpm dlx shadcn-svelte@latest init
```

```shell
┌   shadcn-svelte  v0.13.0
│
◇  Which style would you like to use?
│  Default
│
◇  Which base color would you like to use?
│  Slate
│
◇  Where is your global CSS file? (this file will be overwritten)
│  src/app.css
│
◇  Where is your Tailwind config located? (this file will be overwritten)
│  tailwind.config.ts
│
◇  Configure the import alias for components:
│  $lib/components
│
◇  Configure the import alias for utils:
│  $lib/utils
│
◇  Config file components.json created
│
◇  Project initialized
│
◇  Dependencies installed with pnpm
│
└  Success! Project initialization completed.
```

```shell
pnpm dlx shadcn-svelte@latest add accordion
```

```shell
┌   shadcn-svelte  v0.13.0
│
◇  Components to install:
│  accordion
│
◇  Ready to install components and dependencies?
│  Yes
│
◇  accordion installed at src/lib/components/ui/accordion
│
◇  Dependencies installed with pnpm
│
└  Success! Component installation completed.
```

<a target="_blank" href="/src/routes/+page.svelte">/src/routes/+page.svelte</a>

```svelte
<script lang="ts">
	import { Accordion } from 'bits-ui';

	import * as ShadcnSvelteAccordion from '$lib/components/ui/accordion';
</script>

<h1 class="border-t-8 border-teal-500">Bit UI Accordion with Render Delegation</h1>
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

<h1 class="border-t-8 border-teal-500">Shadcn-Svelte Accordion with Render Delegation</h1>
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
```

```shell
pnpm dlx shadcn-svelte@latest add pagination
```

```shell
┌   shadcn-svelte  v0.13.0
│
◇  Components to install:
│  pagination
│
◇  Ready to install components and dependencies?
│  Yes
│
◇  pagination installed at src/lib/components/ui/pagination
│
◇  button installed at src/lib/components/ui/button
│
◇  Dependencies installed with pnpm
│
└  Success! Component installation completed.

```

Render Delegation with Bits UI `Pagination` works, however Render Delegation with Shadcn-Svelte `Pagination` does not work.

<a target="_blank" href="/src/routes/+page.svelte">/src/routes/+page.svelte</a>

```svelte
<script lang="ts">
	import { Pagination } from 'bits-ui';

	import * as ShadcnSveltePagination from '$lib/components/ui/pagination';
</script>

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
```

```ts
Property 'builder' does not exist on type '{}'.ts(2339)
const builder: any
```

<img src="/static/Screenshot_20240914_155711.png">
