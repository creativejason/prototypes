<script>
	import { PlayFilledAlt, Bookmark, Video, Checkmark, Share, OverflowMenuVertical, CheckmarkOutline, Star } from '@steeze-ui/carbon-icons'
	import Button from './Button.svelte';
</script>

<div class="actions row">
    <div class="primary row">
        <Button icon={PlayFilledAlt} size="large" style="primary" text="Watch Free" primary />
    </div>
    <div class="row">
        <Button icon={Bookmark} />
        <Button icon={Video} />
        <Button icon={CheckmarkOutline} />
        <Button icon={Share} />
        <Button icon={OverflowMenuVertical} /> 
    </div>  
</div>

<style lang="less">

    .row{
        display: flex;
        flex-flow: row wrap;
        gap:16px;
        align-items: inherit;
        justify-content: center;

        .primary{
            flex:1;
            :global(> button) {
                width: 100%;
            }
            button{
                width: 100%;
            }
        }
    }
    
</style>