<script>
    import Header from "./UI/Header.svelte";
    import MeetupGrid from "./Meetups/MeetupGrid.svelte";
    import EditMeetup from "./Meetups/EditMeetup.svelte";
    import TextInput from "./UI/TextInput.svelte";
    import Button from "./UI/Button.svelte"

    let editMode = false;

    let meetups = [
        {
            id: 'm1',
            title: 'Coding Bootcamp',
            subtitle: 'Learn to code in 2 hours',
            description: 'In this meetup, we will have some experts that teach you how to code.',
            imageUrl: 'https://www.civilized.life/assets/Uploads/27c512c3ec/Denver-Begins-Preparations-For-Cannabis-Use-In-Public-Places-Like-Coffee-Shops__FocusFillWzExNzAsNjU4LCJ5Iiw2MV0.jpg',
            address: 'Block 123 Ang Mo Kio Street 30',
            email: 'code@test.com',
            isFavorite: false
        },
        {
            id: 'm2',
            title: 'Swim Together',
            subtitle: 'Let\'s go for a swim',
            description: 'Let\'s have some swimming together.',
            imageUrl: 'https://www.swimminglessons.com.sg/wp-content/uploads/2011/10/Jurong-East-SC-2.png',
            address: 'Jurong East Swimming Complex',
            email: 'code@test.com',
            isFavorite: false
        }
    ];

    function addMeetup(event) {
        const newMeetup = event.detail;
        meetups = [newMeetup, ...meetups];
        editMode = false;
    }

    function toggleFavorite(event) {
        const id = event.detail;
        const updatedMeetup = {...meetups.find(e => e.id === id)};
        updatedMeetup.isFavorite = !updatedMeetup.isFavorite;

        const updatedMeetups = [...meetups];
        const meetupIndex = updatedMeetups.findIndex(e => e.id === id);
        updatedMeetups[meetupIndex] = updatedMeetup;
        meetups = updatedMeetups;
    }
</script>

<style>
    main {
        margin-top: 5rem;
    }

    .meetup-controls {
        margin: 1rem;
    }
</style>

<Header />
<main>
    <div class="meetup-controls">
        <Button caption="New Meetup" on:click={()=>(editMode=true)}/>
    </div>
    {#if editMode}
        <EditMeetup on:addmeetup={addMeetup}/>
    {/if}
    <MeetupGrid {meetups} on:togglefavorite="{toggleFavorite}"/>
</main>

