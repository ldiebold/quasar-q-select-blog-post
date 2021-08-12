<template>
  <q-page
    class="flex flex-center"
    padding
  >
    <div
      class="q-gutter-lg"
    >
      <q-card
        class="q-pa-xl bg-grey-1 shadow-1"
        style=" height: 300px; width: 350px;"
      >
        <q-select
          v-model="dog"
          :options="['Panda', 'Lily', 'Moe']"
        />
      </q-card>
      <!-- #1: Object Style Options -->
      <q-card
        class="q-pa-xl bg-grey-1 shadow-1"
        style=" height: 300px; width: 350px;"
      >
        <q-select
          v-model="dogsObjectOptions"
          :options="[
            {
              label: 'Panda',
              value: 1
            },
            {
              label: 'Lily',
              value: 2
            },
            {
              label: 'Moe',
              value: 3
            }
          ]"
        />
      </q-card>
      <!-- #1: Multiple Select! -->
      <q-card
        class="q-pa-xl bg-grey-1 shadow-1"
        style=" height: 300px; width: 350px;"
      >
        <q-select
          v-model="dogsMultiple"
          :options="['Panda', 'Lily', 'Moe']"
          multiple
        />
      </q-card>
      <!-- #1: Making it Sexy!!! -->
      <q-card
        class="q-pa-xl bg-grey-1 shadow-1"
        style=" height: 300px; width: 350px;"
      >
        <q-select
          v-model="dogsPretty"
          label="Selected Dog"
          label-color="purple-8"
          color="purple"
          bg-color="purple-1"
          popup-content-class="text-grey-8"
          options-selected-class="bg-purple-4 text-white"
          :options="['Panda', 'Lily', 'Moe']"
          outlined
        />
      </q-card>
      <!-- #1: Bunch of Other Cool Stuff In One OTT Example -->
      <q-card
        class="q-pa-xl bg-grey-1 shadow-1"
        style=" height: 300px; width: 600px;"
      >
        <q-select
          v-model="dogsOtt"
          for="dog"
          option-label="name"
          option-value="id"
          multiple
          options-dense
          use-chips
          filled
          rounded
          hint="Select a dog"
          color="brown"
          :suffix="dogsOtt.map(dog => dog.sound).join(', ')"
          :loading="false"
          clear-icon
          counter
          :rules="[val => val.length > 1 || 'Please select at least 2 dogs']"
          :options="[
            {
              name: 'Panda',
              id: 1,
              sound: 'rrrruf! Ruf RUF!'
            },
            {
              name: 'Lily',
              id: 2,
              sound: 'Beep!'
            },
            {
              name: 'Moe',
              id: 3,
              sound: 'Aroooooooo'
            }
          ]"
        />
      </q-card>
      <!-- #1: Improving Performance of Looooong Lists -->
      <q-card
        class="q-pa-xl bg-grey-1 shadow-1"
        style=" height: 450px; width: 350px;"
      >
        <q-select
          v-model="longList"
          popup-content-style="height: 300px;"
          :options="Array.from(Array(1000000).keys())"
          multiple
        />
      </q-card>
      <!-- #1: Extend it to the Nth Degree with Slots -->
      <q-card
        class="q-pa-xl bg-grey-1 shadow-1"
        style=" height: 400px; width: 350px;"
      >
        <q-select
          v-model="slotDog"
          label
          filled
          :options="[
            {
              name: 'Panda',
              color: 'grey-4',
            },
            {
              name: 'Lily',
              color: 'yellow-8',
            },
            {
              name: 'Moe',
              color: 'brown',
            }
          ]"
        >
          <!-- Add an icon WITHIN the input -->
          <template #prepend>
            <q-icon name="pets" />
          </template>
          <!-- Add an icon AFTER the input  -->
          <template #after>
            <q-icon
              v-if="slotDog"
              color="green"
              name="check_circle"
            />
          </template>
          <!-- We can take total control of the label... -->
          <template #label>
            Favourite Dog
            <q-icon
              size="xs"
              name="favorite"
            />
          </template>
          <!-- We can take total control of how options are rendered... -->
          <template #option="scope">
            <q-item
              clickable
              @click="scope.toggleOption(scope.opt)"
            >
              <q-item-section side>
                <q-checkbox
                  :model-value="scope.selected"
                  @click="scope.toggleOption(scope.opt)"
                />
              </q-item-section>
              <q-item-section>
                {{ scope.opt.name }}
              </q-item-section>
            </q-item>
          </template>
          <!-- We can change how the selection is displayed! -->
          <template #selected>
            <div
              v-if="slotDog"
              class="flex items-center"
            >
              <q-icon
                class="q-mr-xs"
                size="xs"
                name="circle"
                :color="slotDog.color"
              />{{ slotDog.name }}
            </div>
          </template>
          <!-- Hooking into the top of our options list is easy! -->
          <template #before-options>
            <q-item-label header>
              Favourite Dog <q-icon name="favorite" />
            </q-item-label>
          </template>
          <!-- And hooking into AFTER our options is peasy! -->
          <template #after-options>
            <q-btn
              v-close-popup
              class="full-width"
              label="cancel"
            />
          </template>
        </q-select>
      </q-card>
      <!-- What Else Is Covered On QuasarComponents.Com?... -->
      <!-- https://quasarcomponents.com -->
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'PageIndex',

  data () {
    return {
      slotDog: null,
      dog: null,
      dogsPretty: null,
      dogsObjectOptions: null,
      dogsMultiple: [],
      dogsOtt: [],
      longList: []
    }
  }
})
</script>
