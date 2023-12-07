<template>
  <div>
    <h1>Hello, This is <b>page/blog</b></h1>
    <table table-auto class="w-full">
      <thead>
        <tr>
          <td class="border px-4 py-2" v-for="key in Object.keys(posted[0])">{{ key }}</td>
        </tr>
      </thead>
      <tbody>
        <tr v-for="tBody in posted">
          <td v-for="tHeadKey in Object.keys(posted[0])">
            <span v-for="tBodyKey in Object.keys(tBody)">{{ tHeadKey === tBodyKey ? tBody[tBodyKey] : "" }}</span>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup lang="ts">
type TPost = {
  userId: number
  id: number
  title: string
  body: string
  [key: string]: string | number // ini dilakukan agar dapat mengakses key dari objek yang berti data TPost
}

const posted : TPost[] = await $fetch<TPost[]>('https://jsonplaceholder.typicode.com/posts').catch((error) => error.data)

</script>