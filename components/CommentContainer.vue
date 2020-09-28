<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <Comment :reply="postData" />
      </div>
    </div>
  </div>
</template>

<script>
import Comment from './Comment'
export default {
  data() {
    return {
      postData: {
        id: 1,
        label: 'Main Comment',
        content:
          'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Asperiores natus veniam perspiciatis error consectetur suscipit deserunt ad. Aperiam, magnam ipsa expedita, impedit ullam eaque totam excepturi natus voluptatem temporibus architect ipsum dolor sit amet consectetur adipisicing elit. Temporibus modi aut inventore, alias tempore voluptatum est eum itaque quos expedita officia ratione, animi nulla repudiandae provident neque aliquid deserunt aperiam.',
        parent: null,
        is_reply: false,
        card: 1,
        created_by: 'Pepe Smith',
        children: [
          {
            id: 2,
            label: 'Reply Comment',
            content:
              'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Asperiores natus veniam perspiciatis error consectetur suscipit deserunt ad. Aperiam, magnam ipsa expedita, impedit ullam eaque totam excepturi natus voluptatem temporibus architect ipsum dolor sit amet consectetur adipisicing elit. Temporibus modi aut inventore, alias tempore voluptatum est eum itaque quos expedita officia ratione, animi nulla repudiandae provident neque aliquid deserunt aperiam.',
            parent: 1,
            is_reply: true,
            card: 1,
            created_by: 'Mike Hanopol',
            children: [
              {
                id: 4,
                label: 'Another Reply To Comment 2',
                content:
                  'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Asperiores natus veniam perspiciatis error consectetur suscipit deserunt ad. Aperiam, magnam ipsa expedita, impedit ullam eaque totam excepturi natus voluptatem temporibus architect ipsum dolor sit amet consectetur adipisicing elit. Temporibus modi aut inventore, alias tempore voluptatum est eum itaque quos expedita officia ratione, animi nulla repudiandae provident neque aliquid deserunt aperiam.',
                parent: 2,
                is_reply: true,
                card: 1,
                created_by: 'Chito Miranda',
                children: [],
              },
              {
                id: 5,
                label: 'Another Reply To Comment 2',
                content:
                  'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Asperiores natus veniam perspiciatis error consectetur suscipit deserunt ad. Aperiam, magnam ipsa expedita, impedit ullam eaque totam excepturi natus voluptatem temporibus architect ipsum dolor sit amet consectetur adipisicing elit. Temporibus modi aut inventore, alias tempore voluptatum est eum itaque quos expedita officia ratione, animi nulla repudiandae provident neque aliquid deserunt aperiam.',
                parent: 2,
                is_reply: true,
                card: 1,
                created_by: 'Hyun Jin',
                children: [],
              },
            ],
          },
          {
            id: 3,
            label: 'Reply Comment 2',
            content:
              'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Asperiores natus veniam perspiciatis error consectetur suscipit deserunt ad. Aperiam, magnam ipsa expedita, impedit ullam eaque totam excepturi natus voluptatem temporibus architect ipsum dolor sit amet consectetur adipisicing elit. Temporibus modi aut inventore, alias tempore voluptatum est eum itaque quos expedita officia ratione, animi nulla repudiandae provident neque aliquid deserunt aperiam.',
            parent: 1,
            is_reply: true,
            card: 1,
            created_by: 'Young K',
            children: [],
          },
        ],
      },
    }
  },
  components: {
    Comment,
  },
}
</script>

<style lang="scss" scoped></style>
