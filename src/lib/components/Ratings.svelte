<script>
    import { Icon } from '@steeze-ui/svelte-icon';
	import { Star } from '@steeze-ui/carbon-icons';
	import Button from './Button.svelte';
	
</script>

<div>
<div class="ratings">
    <div><Icon src={Star} size="20px" />6.2</div>
    <div><Icon src={Star} size="20px" />88%</div>
    <div><Icon src={Star} size="20px" />88%</div>
</div>
<Button text="Rate & Review" size="small" />
</div>

<style lang="less">

    .ratings{
		display: flex;
		flex-flow: row wrap;
		justify-items: center;
		justify-content: center;
		align-items: center;
		align-content: center;
		font-size: .9em;
		gap:16px;

		>div{
			display: inline-flex;
  			align-items: inherit;
			gap:4px;
		}
	}
    
</style>