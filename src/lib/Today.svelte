<script lang="ts">
    import moment from 'moment';

    const today = moment().format('dddd D MMMM');
</script>

<main>
    <div class="today">Today is...</div>
    <h1> {today} </h1>
</main>

<style>
</style>