<script lang="ts">
  import {
    Container,
    CurrencyField,
  } from './lib/components';
  import packageSettings from '../package.json';

  let budget = 0;

  function setBudget(event: CustomEvent) {
    budget = event.detail;
  }
</script>

<Container>
  <h2 style:margin="0 0 20px">
    Buy vs Rent calculator
    <small style:font-size="0.3em">
      v{packageSettings.version}
    </small>
  </h2>

  <CurrencyField
      label="Savings"
      value={10}
      on:change={setBudget}
  />
</Container>