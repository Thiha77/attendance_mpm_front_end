<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
    import { fields } from '../../store';

    export let name;
    export let description;
    
    function saveRole()
    {
        dispatch('saveRole');
    }

    function resetRole()
    {
       name = "";
       description = ""; 
    }
</script>
<style>
	
</style>
<div class="container">
    <div class="row">
        <div class="col mx-auto">
            <div class="card card-mpm1">
                <div class="card-heading bg-blue-mpm p-3">
                    <h3 class="text-white text-uppercase text-center">{$fields.role.form.createTitle}</h3>
                </div>
                <div class="card-body p-5">
                    <div class="form-group">
                        <label for="name">{$fields.role.role.name}:</label>
                        <input type="text" bind:value={name} class="form-control" placeholder={$fields.role.placeholder.name} name="name">
                    </div>
                    <div class="form-group">
                        <label for="desc">{$fields.role.role.description}:</label>
                        <textarea  bind:value={description} class="form-control" placeholder={$fields.role.placeholder.description} name="desc"></textarea>
                    </div>
                    <div class="mt-4">
                        <!-- <a href="role" class="btn btn-danger">{$fields.form.back}</a>   -->
                        <button type="submit" class="btn btn-blue" on:click={saveRole}>{$fields.role.form.save}</button>
                        <button type="reset" class="btn btn-outline-orange" on:click={resetRole}>{$fields.role.form.cancel}</button>     
                    </div>
                </div><!-- .card-body -->
            </div><!-- .card -->
        </div>
    </div>
</div>