<script>
    import { createEventDispatcher } from "svelte";
    import TextInput from "../UI/TextInput.svelte";
    import Button from "../UI/Button.svelte";

    const dispatch = createEventDispatcher();
    const meetup = {
        title: "",
        subtitle: "",
        address: "",
        email: "",
        description: "",
        imageUrl: ""
    };
</script>

<style>
    form {
        width: 30rem;
        max-width: 90%;
        margin: auto;
    }
</style>

<form on:submit|preventDefault="{() => dispatch("addmeetup", meetup)}">
    <TextInput 
        id="title"
        label="Title"
        value={meetup.title}
        on:input="{event => (meetup.title = event.target.value)}"
    />
    <TextInput 
        id="subtitle"
        label="Subtitle"
        value={meetup.subtitle}
        on:input="{event => (meetup.subtitle = event.target.value)}"
    />
    <TextInput 
        id="address"
        label="Address"
        value={meetup.address}
        on:input="{event => (meetup.address = event.target.value)}"
    />
    <TextInput 
        id="imageUrl"
        label="Image URL"
        value={meetup.imageUrl}
        on:input="{event => (meetup.imageUrl = event.target.value)}"
    />
    <TextInput 
        id="email"
        label="E-Mail"
        value={meetup.email}
        on:input="{event => (meetup.email = event.target.value)}"
        type={"email"}
    />
    <TextInput 
        id="description"
        label="Description"
        value={meetup.description}
        on:input="{event => (meetup.description = event.target.value)}"
        controlType={"textarea"}
    />
    <Button type="submit" caption="Add" />
</form>