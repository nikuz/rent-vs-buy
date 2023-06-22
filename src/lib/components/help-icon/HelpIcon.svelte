<script lang="ts">
    import Tooltip, { Wrapper } from '@smui/tooltip';
    import Icon from '@smui/textfield/icon';
</script>

<Wrapper>
    <div class="help-icon-wrapper">
        <Icon class="material-icons">help</Icon>
    </div>
    <Tooltip>
        <slot></slot>
    </Tooltip>
</Wrapper>

<style>
    .help-icon-wrapper {
        display: inline-flex;
        border-radius: 50%;
    }

    .help-icon-wrapper:hover {
        background-color: rgba(0, 0, 0, 0.04);
    }

    @media (prefers-color-scheme: dark) {
        .help-icon-wrapper:hover {
            background-color: rgba(255, 255, 255, 0.08);
        }
    }
</style>