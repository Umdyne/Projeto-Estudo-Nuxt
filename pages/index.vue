<template>
    <div class="w-full px-2 ">
        
        <ListItem v-for="contact in contacts" :key="contact.id">
        {{  contact.name }}
       
        <template #actions>
            <button @click="editContact(contact.id)">Editar</button>
            <button @click="removeContact(contact.id)">Excluir</button>
        </template>
       </ListItem>
    </div>
    
    <UIButton @click="addContato">Adicionar </UIButton>
</template>

<script setup>
const router = useRouter();
const { contactList, deleteContact } = useContacts()
const contacts = contactList

useHead({
    title: "Contatos.com",
    meta: [
        { name: "description" , content: "Listador de contatos"},
        //facebook
        { name: "facebook:title", content: "Listador de contatos"},
        //General SEO
        { property: "og:title", content: "Listador de contatos"}

    ]
})

const addContato = () => {
    router.push("/form")
}
const editContact = (id) => {
    router.push({ path: "/form", query: { id } })
}

const removeContact = id => {
    deleteContact(id);
}

</script>