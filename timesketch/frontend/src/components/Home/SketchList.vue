<!--
Copyright 2019 Google Inc. All rights reserved.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->
<template>
  <div>
    <b-table
      :data="sketches"
      :per-page="10"
      paginated
      pagination-simple
      pagination-position="bottom"
      default-sort-direction="desc"
      icon-pack="fas"
      icon-prev="chevron-left"
      icon-next="chevron-right">
      <template slot-scope="props">
        <b-table-column field="name" label="Name">
          <router-link :to="{ name: 'SketchOverview', params: {sketchId: props.row.id } }"><strong>{{ props.row.name }}</strong></router-link>
        </b-table-column>
        <b-table-column field="user" label="Created by" width="200">
          {{ props.row.user }}
        </b-table-column>
        <b-table-column field="updated_at" label="Last activity" width="200">
          {{ new Date(props.row.updated_at) | moment("YYYY-MM-DD HH:mm") }}
        </b-table-column>
      </template>
    </b-table>
  </div>
</template>

<script>
export default {
  props: ['sketches']
}
</script>

<!-- CSS scoped to this component only -->
<style scoped lang="scss"></style>
