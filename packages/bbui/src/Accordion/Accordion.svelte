<script>
  import "@spectrum-css/accordion"

  export let itemName = undefined
  export let initialOpen = false
  export let header
  export let bold = true
  export let noPadding = false

  let isOpen = initialOpen

  function getOpenClass(isOpen) {
    return isOpen ? "is-open" : ""
  }
</script>

<div class="spectrum-Accordion" role={itemName}>
  <div class="spectrum-Accordion-item {getOpenClass(isOpen)}">
    <h3 class="spectrum-Accordion-itemHeading">
      <button
        class="spectrum-Accordion-itemHeader"
        type="button"
        style="--font-weight: {bold ? 'bold' : 'normal'}"
        on:click={() => (isOpen = !isOpen)}
      >
        {header}
      </button>
      <svg
        class="spectrum-Icon spectrum-UIIcon-ChevronRight100 spectrum-Accordion-itemIndicator"
        focusable="false"
        aria-hidden="true"
      >
        <use xlink:href="#spectrum-css-icon-Chevron100" />
      </svg>
    </h3>
    <div
      class="spectrum-Accordion-itemContent"
      role={itemName}
      style={noPadding
        ? "padding-left: 20px; padding-bottom: 0;"
        : "padding-left: 30px;"}
    >
      <slot />
    </div>
  </div>
</div>

<style>
  .spectrum-Accordion {
    margin-left: -20px;
  }
  .spectrum-Accordion-item {
    border: none;
  }
  .spectrum-Accordion-itemContent {
    width: 97%;
  }
  .spectrum-Accordion-itemHeader {
    text-transform: none;
    font-weight: var(--font-weight);
    font-size: 0.875rem;
    min-height: auto;
  }
</style>
