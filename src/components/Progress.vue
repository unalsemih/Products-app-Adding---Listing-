<template>
    <div class="progress">
        <div class="progress-bar bg-info" role="progressbar" :style="{ width: progressValue + '%' }" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100">
        {{ currentItem }}/10
        </div>
    </div>
</template>

<script>
import { eventBus } from '../main';

export default ({
    data(){
        return {
            currentItem: null,
            progressValue: null
        }
    },
    created () {
        eventBus.$on('progressBarUpdated', (productListCount) => {
            this.currentItem = productListCount;
            this.progressValue = productListCount * 10;
        })
    }
})
</script>
