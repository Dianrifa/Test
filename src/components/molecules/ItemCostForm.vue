<template>
  <tr>
    <td>
      <BaseInput
        type="text"
        placeholder="description"
        :name="id + 'description'"
      />
    </td>
    <td>
      <div class="w-20">
        <BaseInput type="number" placeholder="Qty" :name="id + 'qty'" />
      </div>
    </td>
    <td>
      <div class="w-20">
        <BaseSelect :options="this.$store.state.uom" :name="id + 'uom'" />
      </div>
    </td>
    <td>
      <div class="w-28">
        <BaseInput type="number" placeholder="Unit Price" :name="id + 'unit'" />
      </div>
    </td>
    <td>
      <div class="w-28">
        <BaseInput
          type="number"
          placeholder="Discount"
          :name="id + 'discount'"
        />
      </div>
    </td>
    <td>
      <div class="w-28">
        <BaseInput type="number" placeholder="VAT" :name="id + 'vat'" />
      </div>
    </td>
    <td>
      <div class="w-20">
        <BaseSelect
          :options="this.$store.state.currency"
          :name="id + 'currency'"
        />
      </div>
    </td>
    <td><div class="w-24">0.00</div></td>
    <td><div class="w-20">0.00</div></td>
    <td><div class="w-20">0.00</div></td>
    <td>
      <div class="w-full flex items-center gap-2">
        <BaseSelect
          :options="[
            { name: 'Select an option', value: 'default' },
            ...this.$store.state.banks,
          ]"
        />
        <BaseButton
          icon="minus"
          type="secondary"
          size="medium"
          :onClick="onRemoveItemForm"
        />
      </div>
    </td>
  </tr>
</template>

<script>
import BaseInput from "../atomic/Input.vue";
import BaseSelect from "../atomic/Select.vue";
import BaseButton from "../atomic/Button.vue";

export default {
  name: "ItemCostForm",
  components: { BaseButton, BaseSelect,BaseInput },
  props: {
    onRemoveItemForm: Function,
    id: String,
  },
  data() {
    return {
      currencySelected: "",
      description: "",
    };
  },
};
</script>

<style lang="scss" scoped>
tr {
  @apply border-gray-200 border-2;

  td {
    @apply p-2 text-left text-gray-500;
  }
}
</style>
