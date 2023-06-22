<script lang="ts">
    import { createEventDispatcher } from 'svelte';
    import Select, { Option } from '@smui/select';
    import type { Compound } from '../../types';

    // props
    export let value: Compound;
    export let style: string | undefined = undefined;

    const dispatch = createEventDispatcher();

    function onChange(event) {
        dispatch('change', event.detail.value);
    }
</script>

<Select
    variant="outlined"
    label="Compound"
    {style}
    bind:value
    on:SMUISelect:change={onChange}
>
    <Option value="annually">Annually</Option>
    <Option value="monthly">Monthly</Option>
</Select>