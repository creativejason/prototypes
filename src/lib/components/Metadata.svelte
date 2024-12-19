<script>
    import { Icon } from '@steeze-ui/svelte-icon';
	import { BookmarkFilled, Star, StarFilled } from '@steeze-ui/carbon-icons';
	import Button from './Button.svelte';
	import Badge from './badge.svelte';
	
</script>

<div class="metadata">
    <div class="row attributes">
        <div class="row badges">
            <Badge text="PG-13" />
            <Badge icon={BookmarkFilled} text="In Watchlist" />
        </div>
        2015 1hr 52min Sci-Fi, Fantasy
    </div>
    <div class="row ratings">
		<span><Icon src={StarFilled} size="20px" />6.2</span>
		<span><Icon src={StarFilled} size="20px" />88%</span>
		<span><Icon src={StarFilled} size="20px" />88%</span>
		<Button text="Rate & Review" size="small" />
	</div>	
</div>

<style lang="less">

    .metadata{
		display: flex;
		flex-flow: column nowrap;
		justify-content: center;
		align-items:inherit;
		gap: 8px;
	}
	
	.row{
		display: flex;
		flex-flow: row wrap;
		justify-content: center;
		align-items: center;
		gap: 8px;
	}

	.ratings{

		>span{
			display: inline-flex;
  			align-items: center;
			gap:4px;
			font-size: small;
			line-height: 20px;
		}
	}
    
</style>