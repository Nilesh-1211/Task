<template>
    <div class="slider">
        <div class="slider_bar" ref="bar">
            <div class="slider_handle" :style="handleStyle" ref="handle"></div>
            <div class="slider_fill" :style="fillStyle"></div>
        </div>
    </div>
</template>

<script>
import "./slider.scss"
import throttle from 'lodash/throttle';
export default{
    props:{
        min:{
            type: Number,
            default:0
        },
        max:{
            type: Number,
            default:1
        },

        value: Number,
        disabled: Boolean
    },
    name:"Slider",
    data: () => ({
        isDragging: false,
        handleWidth: 0,
        barWidth: 0,
    }),
    
    computed:{
        delta(){
            return this.value/this.max;
        },
        fillStyle(){
            return {
                transformOrigin: 'left center',
                transform: `scaleX(${this.delta})`
            };
        },
        handleStyle(){
            const {barWidth,delta,handleWidth}=this;
            return {
                transform: `translateX(${barWidth * delta - (handleWidth * 0.5)}px)`
            };
        }
    },

    mounted(){
        this.onWindowResize=throttle(this.onWindowResize,200)
        this.calcDimensions();
        window.addEventListener("resize",this.onWindowResize);
    },

    methods:{
        onWindowResize(){
            this.calcDimensions();
            console.log(this.barWidth);
        },
        calcDimensions(){
            const { bar, handle } =this.$refs;
            
            this.handleWidth=handle.offsetWidth;
            this.barWidth=bar.offsetWidth;
            console.log(this.handleWidth,this.barWidth);
        }
    }
}
</script>