<template>
  <v-app dark flat>
      <v-app-bar>
        <v-app-bar-title>
          <v-switch location="bottom" @click="toggleTheme"
            v-model="$vuetify.theme.dark"
            inset
            label="Theme"
            persistent-hint
          ></v-switch>
        </v-app-bar-title>
      </v-app-bar>
      <v-main>
        <v-list>
          <v-subheader>I inherit dark from my parent</v-subheader>
          <v-list-item>
            <v-list-item-title>One</v-list-item-title>
          </v-list-item>
          <v-list-item>
            <v-list-item-title>Two</v-list-item-title>
          </v-list-item>
          <v-list-item>
            <v-list-item-title>Three</v-list-item-title>
          </v-list-item>
        </v-list>
        <v-divider class="mb-y"></v-divider>
        <v-theme-provider root>
          <v-list rounded="b">
            <v-subheader>
              <span>I inherit from the root</span>
              <strong>&nbsp;$vuetify.theme.dark</strong>
            </v-subheader>
            <v-list-item>
              <v-list-item-title>One</v-list-item-title>
            </v-list-item>
            <v-list-item>
              <v-list-item-title>Two</v-list-item-title>
            </v-list-item>
            <v-list-item>
              <v-list-item-title>Three</v-list-item-title>
            </v-list-item>
          </v-list>
        </v-theme-provider>
      </v-main>
  </v-app>
</template>

<script setup lang="ts">
import { useTheme } from 'vuetify';

const theme = useTheme();

function toggleTheme () {
  theme.global.name.value = theme.global.current.value.dark ? 'light' : 'dark'
};
</script>