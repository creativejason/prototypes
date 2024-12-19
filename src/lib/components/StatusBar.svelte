<script>
    import { Icon } from '@steeze-ui/svelte-icon'
    import { BatteryFull, SignalStrength, Wifi } from '@steeze-ui/carbon-icons';
	
</script>

<div class="status-bar">
    <span>9:41</span>
    <Icon src={SignalStrength} size="18px"/>
    <Icon src={Wifi} size="18px"/>
    <Icon src={BatteryFull} size="24px"/>
</div>

<style lang="less">
    .status-bar{
        color: white;
		display: flex;
        align-items: center;
        padding:8px 24px 24px 24px;

        span{
            flex:1;
        }
	}
</style>