<script>
    import { Icon } from '@steeze-ui/svelte-icon'
	let {icon, text} = $props();
</script>

<div class="badge">
    {#if icon}
        <Icon src={icon} size="14px" />
    {/if}
    {#if text}
        <span>{text}</span>
    {/if}
</div>

<style lang="less">
    .badge{
		display: flex;
		flex-flow: row nowrap;
		align-items: center;
		gap:4px;
		background-color: rgba(0, 0, 0, 0.8);
		font-size: .9em;
		font-weight: bold;
		padding: 4px 8px;
		border-radius: 4px;
	}
</style>