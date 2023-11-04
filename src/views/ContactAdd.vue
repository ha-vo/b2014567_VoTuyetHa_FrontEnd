
<template>
    <div class="page">
        <h4>Thêm liên hê mới</h4>
        <ContactForm :contact="contact" @submit:contact="updateContact" />
        <p>{{ message }}</p>
    </div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
    components: {
        ContactForm,
    },

    data() {
        return {
            contact: null,
            message: "",
        };
    },
    methods: {
        async updateContact(data) {
            try {
                await ContactService.create(data);
                this.message = "Tạo liên hệ mới thành công";
            } catch (error) {
                console.log(error);
            }
        },

    },
    created() {
        this.contact = {
            name: "",
            phone: "",
            email: "",
            address: "",
            favorite: false
        }
    }

};
</script>