<script>
	
</script>

<div class="social-proof">
    <div class=avatars>
        <img class="avatar" src="images/responsive-details/avatar1.jpg" alt="avatar" />
        <img class="avatar" src="images/responsive-details/avatar2.jpg" alt="avatar" />
        <img class="avatar" src="images/responsive-details/avatar3.jpg" alt="avatar" />
    </div>
    <div class="summary">Watched by Cpt. Pike, Spock + 21 others</div>
</div>

<style lang="less">

    .social-proof{
		display: flex;
		flex-flow: row wrap;
		justify-items: center;
		justify-content: center;
		align-items: center;
		align-content: center;
        font-size: .9em;
		gap:8px;

		.avatars{
			display: flex;
			flex-flow: row wrap;
			justify-items: center;
			justify-content: center;
			align-items: center;
			align-content: center;
			height: 40px;

			.avatar{
				border-radius: 999px;
				background-color: rgb(58, 58, 58);
				width: 40px;
				height: 40px;
				margin-left:-12px;
				border:solid 1px black;
				&:first-child{
					margin-left:0px;
				}
			}
		}

		.summary{
			flex: 1;
			min-width: 128px;
		}
	}
    
</style>