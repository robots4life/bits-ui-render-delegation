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
