<script context="module" lang="ts">
	export { default as BaseTabItem } from "./shared/TabItem.svelte";
</script>

<script lang="ts">
	import type { Gradio, SelectData } from "@gradio/utils";
	import TabItem from "./shared/TabItem.svelte";

	export let elem_id = "";
	export let elem_classes: string[] = [];
	export let label: string;
	export let id: string | number;
	export let gradio:
		| Gradio<{
				select: SelectData;
		  }>
		| undefined;
	export let visible = true;
	export let interactive = true;
	export let order: number;
	export let scale: number;
</script>

<TabItem
	{elem_id}
	{elem_classes}
	{label}
	{visible}
	{interactive}
	{id}
	{order}
	{scale}
	on:select={({ detail }) => gradio?.dispatch("select", detail)}
>
	{#if visible}
		<slot />
	{/if}
</TabItem>
