<script lang="ts">
    import {
        createEventDispatcher,
        onMount,
    } from 'svelte';
    import TextField from '@smui/textfield';

    export let value: string;
    export let label: string;

    const dispatch = createEventDispatcher();
    const currencyFormatter = new Intl.NumberFormat('en-US', {
        style: 'currency',
        currency: 'USD',
        minimumFractionDigits: 0,
        maximumFractionDigits: 0,
    });

    function onChange(event: Event) {
        const target = event.target as HTMLInputElement;
        console.log(target.value);
        value = currencyFormatter.format(target.value);

        dispatch('change', Number(target.value));
    }

    onMount(async () => {
        if (value !== undefined) {
            value = currencyFormatter.format(value);
        }
    });
</script>

<TextField
    variant="outlined"
    type="string"
    bind:value={value}
    bind:label={label}
    on:change={onChange}
/>