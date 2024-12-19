<script>

    import { Close} from '@steeze-ui/carbon-icons';
    import { Cast, Share } from '@steeze-ui/material-design-icons'
	import Button from './Button.svelte';
	
</script>

<div class="button-bar">
    <div class="left">
        <Button icon={Close} style="dark" />
    </div>
    <div class="right">
        <Button icon={Share} style="dark" />
        <Button icon={Cast} style="dark" />
    </div>    
</div>

<style lang="less">
    
    .button-bar{
		display: flex;
        flex-flow: row wrap;
        align-items: inherit;
        padding:16px 24px;
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        z-index: 1;
	}

    .left{
        flex: 1;
        display: flex;
        flex-flow: row nowrap;
        justify-content: start;
        gap:8px;
    }

    .right{
        flex: 1;
        display: flex;
        flex-flow: row nowrap;
        justify-content: end;
        gap:8px;
    }
</style>