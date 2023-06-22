<script lang="ts">
    import { createEventDispatcher } from 'svelte';
    import TextField from '@smui/textfield';
    import Icon from '@smui/textfield/icon';

    interface $$Props {
        value: number,
        label: string,
    }

    // props
    export let value: number;
    export let label: string;
    export let min: number | undefined;
    export let max: number | undefined;
    export let adornment: string | undefined;
    export let style: string | undefined = undefined;

    const dispatch = createEventDispatcher();
    function onChange(event: InputEvent) {
        const target = event.target as HTMLInputElement;
        let newValue = Number(target.value);

        if (min !== undefined && newValue < min) {
            newValue = min;
            value = min;
        }
        if (max !== undefined && newValue > max) {
            newValue = max;
            value = max;
        }

        dispatch('change', newValue);
    }
</script>

<TextField
    variant="outlined"
    type="number"
    {label}
    {style}
    bind:value={value}
    on:input={onChange}
>
    <svelte:fragment slot="trailingIcon">
        {#if adornment}
            <Icon class="material-icons">{adornment}</Icon>
        {/if}
    </svelte:fragment>
</TextField>