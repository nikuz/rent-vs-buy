<script lang="ts">
    import {
        createEventDispatcher,
        onMount,
    } from 'svelte';
    import TextField from '@smui/textfield';

    // props
    export let value: number;
    export let label: string;
    export let style: string | undefined;

    let valueString: string = '';
    const dispatch = createEventDispatcher();
    const currencyFormatter = new Intl.NumberFormat('en-US', {
        style: 'currency',
        currency: 'USD',
        minimumFractionDigits: 0,
        maximumFractionDigits: 0,
    });

    function getFormattedValuePart(value: number): string {
        return currencyFormatter.format(value).replace(/\d+/g, '');
    }

    function onChange(event: InputEvent) {
        const currencySign = getFormattedValuePart(1);
        const digitSeparator = getFormattedValuePart(1111).replace(currencySign, '');

        if (!Number.isNaN(Number(event.data))) {
            value = Number(valueString.replace(currencySign, '').replace(new RegExp(digitSeparator, 'g'), ''));
            dispatch('change', value);
        }

        valueString = currencyFormatter.format(value);
    }

    onMount(async () => {
        if (value !== undefined) {
            valueString = currencyFormatter.format(value);
        }
    });
</script>

<TextField
    variant="outlined"
    type="string"
    label={label}
    bind:value={valueString}
    style={style}
    on:input={onChange}
/>