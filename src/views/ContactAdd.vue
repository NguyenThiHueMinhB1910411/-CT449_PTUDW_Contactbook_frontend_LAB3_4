<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
    components: { ContactForm },

    data() {
        return {
            contact: {
                _id: "",
                address: "",
                email: "",
                favorite: null,
                name: "",
                phone: "",
            },
            message: "",
        };
    },
    
    methods: {
        async addContact(data) {
            try {
                console.log(data);
                await ContactService.create(data);
                this.message = "Thêm liên hệ thành công !";
            } catch (error) {
                console.log(error);
            }
        },
    },
};


</script>

<template>
    <div class="page">
        <h4 class="text-primary">Thêm liên hệ</h4>
        <ContactForm :contact="contact" @submit:contact="addContact" />
        <p>{{ message }}</p>
    </div>
</template>

<style>

</style>