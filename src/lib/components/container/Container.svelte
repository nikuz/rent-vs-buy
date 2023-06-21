<main class="page-container">
    <slot></slot>
</main>

<style>
    .page-container {
        margin: 0 auto;
        padding: 16px;
    }

    @media (min-width: 1200px) {
        .page-container {
            max-width: 1200px;
        }
    }

    @media (min-width: 600px) {
        .page-container {
            padding: 16px 24px;
        }
    }
</style>
