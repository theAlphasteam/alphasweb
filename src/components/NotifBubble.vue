<template>
    <div class="bubble glass glass--bg" :class="{active : active, error : bubbleData.status.toLowerCase() == 'error'}">
        <h3>{{bubbleData.status}}</h3>
        <p>{{bubbleData.message}}</p>
    </div>

    <!-- <div class="notif-bubble glass glass--bg">
    </div> -->
</template>

<script>
    export default {
        name: "NotifBubble",
        props:{
            bubbleData: Object
        },
        data(){
            return{
                active: false
            }
        },
        watch:{
            bubbleData(){
                this.active = true;
                setTimeout(()=>{
                    this.active = false
                }, 6000)
            }
        }
    }

</script>

<style lang="scss" scoped>
    @import "@/scss/_utils.scss";

    .bubble {
        position: fixed;
        bottom: 0;
        left: 50%;
        transform: translate(-50%, 100%);

        min-width: 120px;
        min-height: 40px;

        display: flex;
        align-items: flex-start;
        justify-content: center;
        padding: 0.5em;
        gap: $defValEm;
        border-radius: $defValpx;

        &.active {
            transform: translate(-50%, -100%);
        }

        &.error {
            background: var(--warning-trans);
            border-color: var(--warning-trans-blur);
        }
    }
</style>