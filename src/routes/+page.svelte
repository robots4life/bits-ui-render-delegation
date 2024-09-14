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
