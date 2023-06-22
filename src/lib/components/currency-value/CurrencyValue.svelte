<script lang="ts">
    // props
    export let value: number;
    export let style: string | undefined = undefined;

    const currencyFormatter = new Intl.NumberFormat('en-US', {
        style: 'currency',
        currency: 'USD',
        minimumFractionDigits: 0,
        maximumFractionDigits: 0,
    });
</script>

<span {style}>
    {currencyFormatter.format(value)}
</span>