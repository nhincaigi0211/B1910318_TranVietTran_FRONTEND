<template>
    <div v-if="contact" class="page">
        <h4> Tạo liên hệ mới</h4>
        <ContactForm :contact="contact" @submit:contact="contactCreate" />
        <p>{{ message }}</p>
    </div>
</template>

<script>
import ContactForm from '../components/ContactForm.vue';
import ContactService from '../services/contact.service';
export default {
    components: {
        ContactForm
    },

    props: {
        contact: { type: String, required: true },
    },

    data() {
        return {
            contact: {},
            message: ""
        }
    },

    methods: {
        async contactCreate(data) {
            try {
                await ContactService.create(data)
                this.message = "Liên hệ được tạo thành công"
            }
            catch (error) {
                console.log(error)
            }
        },

    },
}
</script>