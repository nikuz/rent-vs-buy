<script lang="ts">
  import {
    Container,
    CurrencyField,
    CurrencyValue,
    NumericField,
    CompoundSelector,
  } from './lib/components';
  import type { Compound } from './lib/types';
  import packageSettings from '../package.json';

  let budget = 0;
  function setBudget(event: CustomEvent) {
    budget = event.detail;
  }

  let investmentReturnRate = 0;
  function setInvestmentReturnRate(event: CustomEvent) {
    investmentReturnRate = event.detail;
  }

  let compound: Compound = 'annually';
  function setCompound(event: CustomEvent) {
    compound = event.detail;
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
      value={10000}
      on:change={setBudget}
  />

  <CurrencyValue
      value={10000}
  />

  <NumericField
      label="Investment return rate"
      value={8}
      min={0}
      max={10}
      style="width: 150px"
      adornment="percent"
      on:change={setInvestmentReturnRate}
  />

  <CompoundSelector
      value={compound}
      on:change={setCompound}
  />
</Container>