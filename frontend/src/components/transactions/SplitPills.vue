<!--
  - SplitPills.vue
  - Copyright (c) 2021 james@firefly-iii.org
  -
  - This file is part of Firefly III (https://github.com/firefly-iii).
  -
  - This program is free software: you can redistribute it and/or modify
  - it under the terms of the GNU Affero General Public License as
  - published by the Free Software Foundation, either version 3 of the
  - License, or (at your option) any later version.
  -
  - This program is distributed in the hope that it will be useful,
  - but WITHOUT ANY WARRANTY; without even the implied warranty of
  - MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
  - GNU Affero General Public License for more details.
  -
  - You should have received a copy of the GNU Affero General Public License
  - along with this program.  If not, see <https://www.gnu.org/licenses/>.
  -->

<template>
  <div>
    <div v-if="transactions.length > 1" class="row">
      <div class="col">
        <!-- tabs -->
        <ul class="nav nav-pills ml-auto p-2" id="transactionTabs">
          <li v-for="(transaction, index) in this.transactions" class="nav-item"><a :class="'nav-link' + (0 === index ? ' active' : '')"
                                                                                    :href="'#split_' + index"
                                                                                    :id="'tab_split_' + index"
                                                                                    data-toggle="pill">
            <span v-if="'' !== transaction.description">{{ transaction.description }}</span>
            <span v-if="'' === transaction.description">Split {{ index + 1 }}</span>
          </a></li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SplitPills",
  props: {
    transactions: {
      type: Array,
      required: true,
      default: function () {
        return [];
      }
    },
    count: {
      type: Number,
      required: true
    },
  }
}
</script>
