<script>
import { createEventDispatcher } from 'svelte';
import { fields } from '../../store';
const dispatch = createEventDispatcher();

let textSearch;

const search = () => {
    dispatch('search',{textSearch : textSearch});
};

</script>

<form>
    <div class="input-group">
        <input class="form-control" bind:value={textSearch} type="text" placeholder={$fields.notice.placeholder.search} aria-label="Search" />
        <div class="input-group-append">
            <button type="submit" class="input-group-text" on:click|preventDefault={search}><i class="fas fa-search text-grey" aria-hidden="true"></i></button>
        </div>
    </div>
</form>