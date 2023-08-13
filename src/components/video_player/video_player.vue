<template>
    <div class="video_player">
        <div class="player_sizer">
            <video id ="player" controls>
                <source type="video/mp4" src="@/assets/video.mp4"/>
                <track
                label="English"
                kind="subtitles"
                srclang="en"
                src="@/assets/subtitle.vtt"
                default />
            </video>
        </div>
    </div>
</template>

<script>
    import "./video_player.scss"
    export default{
        name:"video_player"
    }
</script>