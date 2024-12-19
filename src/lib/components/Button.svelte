<script>
    import { Icon } from '@steeze-ui/svelte-icon'
	let {icon, text, size = "medium", style = "default"} = $props();
</script>

<button class="button {size} {style}">
    {#if icon}
        <Icon src={icon} size="20px" />
    {/if}
    {#if text}
        <span>{text}</span>
    {/if}
</button>

<style lang="less">
    .button{
		background-color: rgba(255,255,255,.1);
		color:white;
		border-radius: 999px;
  		border-width: 0;
		display: inline-block;
		font-size: .8em;
		font-weight: 600;
		line-height: 20px;
		list-style: none;
		margin: 0;
		padding: 8px 16px;
		text-align: center;
		transition: all 200ms;
		vertical-align: baseline;
		white-space: nowrap;
		user-select: none;
		-webkit-user-select: none;
		touch-action: manipulation;
		display: inline-flex;
  		align-items: inherit;
		justify-content: center;
		gap: 8px;
		max-width: 320px;

		&.large{
			padding: 8px 24px;
			font-size: 1em;
			line-height: 20px;
		}

		&.small{
			padding: 4px 12px;
			font-size: .px;
			line-height: 18px;
		}

		&.primary{
			background-color: white;
			color:black;
		}

		&.dark{
			background-color: rgb(0, 0, 0, .5);
			color:white;
		}

		&:global(:not(:has(span))){
			padding: 8px;
		}

	}
</style>