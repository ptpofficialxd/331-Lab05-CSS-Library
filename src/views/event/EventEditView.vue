<script setup lang="ts">
import type { Ref } from 'vue'
import type { EventItem } from '@/type';
import { ref, type PropType } from 'vue';
import EventService from '@/services/EventService';
import { useRouter } from 'vue-router';
import { useMessageStore } from '@/stores/message';

const event = ref<EventItem | null>(null)

const props = defineProps({
    event: {
        type: Object as PropType<EventItem>,
        require: true
    }
})

const router = useRouter()
const store = useMessageStore()

function edit() {

    store.updateMessage('You are successfully edited for ' + props.event?.title)
    setTimeout(() => {
        store.resetMessage()
    }, 3000)

    router.push({
        name: 'event-detail',
        params: {
            id: props.event?.id
        }
    })
}

</script>

<template>
    <p class="mt-6 mb-6 font-bold text-2xl">Edit the event here</p>
    <button @click="edit" class="rounded-full px-4 py-2 bg-orange-400 text-xl font-bold text-white">Edit Me</button>
</template>


