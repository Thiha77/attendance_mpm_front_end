<script>
import { createEventDispatcher } from 'svelte';
import { fields } from '../../store';
const dispatch = createEventDispatcher();

let search = {
    text: ""
}

const searchPermission = () => {
    dispatch('searchPermission',{search});
}

</script>

<div class="input-group">
    <input class="form-control" bind:value={search.text} type="text" placeholder={$fields.permission.placeholder.search} aria-label="Search">
    <div class="input-group-append">
        <button class="input-group-text" on:click={searchPermission}><i class="fas fa-search text-grey" aria-hidden="true"></i></button>
    </div>
</div>