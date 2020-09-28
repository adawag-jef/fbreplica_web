<template>
  <div>
    <tree :tree-data="tree"></tree>
  </div>
</template>

<script>
import Tree from './Tree'

export default {
  data: () => ({
    tree: {
      id: 1,
      label: 'Main Comment',
      parent: null,
      is_reply: false,
      card: 1,
      created_by: 3,
      children: [
        {
          id: 2,
          label: 'Reply Comment',
          parent: 1,
          is_reply: true,
          card: 1,
          created_by: 3,
          children: [
            {
              id: 4,
              label: 'Another Reply To Comment 2',
              parent: 2,
              is_reply: true,
              card: 1,
              created_by: 3,
              children: [],
            },
            {
              id: 5,
              label: 'Another Reply To Comment 2',
              parent: 2,
              is_reply: true,
              card: 1,
              created_by: 3,
              children: [],
            },
          ],
        },
        {
          id: 3,
          label: 'Reply Comment 2',
          parent: 1,
          is_reply: true,
          card: 1,
          created_by: 3,
          children: [],
        },
      ],
    },
  }),
  components: {
    Tree,
  },
}
</script>



