<template>
  <div :style="{ textAlign: 'initial' }">
    <div>
      <h2>{{ post.title }}</h2>
      <h3>{{ post.name }}</h3>
      <span>{{ post.date }}</span>
      <a-divider />
      {{ post.content }}
    </div>
    <div :style="{ padding: '8px' }">
      Comments
      <a-input placeholder="Basic usage" />
      <a-list itemLayout="horizontal" :dataSource="data">
        <a-list-item slot="renderItem" slot-scope="item">
          <a-list-item-meta
            description="Ant Design, a design language for background applications, is refined by Ant UED Team"
          >
            <a slot="title" href="https://vue.ant.design/">{{ item.title }}</a>
          </a-list-item-meta>
        </a-list-item>
      </a-list>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

const data = [
  { title: 'Ant Design Title 1' },
  { title: 'Ant Design Title 2' },
  { title: 'Ant Design Title 3' },
  { title: 'Ant Design Title 4' },
];
const post = {
  name: '김아무개',
  date: '2019-01-01',
  title: '안녕하세요',
  content:
    'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent a faucibus nunc, vitae porta nunc. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Interdum et malesuada fames ac ante ipsum primis in faucibus. Maecenas convallis et mi in faucibus. Aenean sollicitudin sapien massa, vitae molestie felis sagittis vel. Nulla bibendum risus ut metus aliquet efficitur. Donec ex libero, fringilla ac pellentesque non, blandit a dolor. Nam sit amet varius mauris, et blandit elit. Ut hendrerit ut dui vitae pharetra. Ut tincidunt neque vitae ante semper, vel efficitur urna rutrum. Cras in dui posuere erat venenatis tempus et nec augue. Ut scelerisque ex a lacus suscipit mollis. Vestibulum vitae lorem velit. Nam dictum lectus quis consectetur sagittis. Etiam semper, magna quis placerat porta, risus risus accumsan mauris, vel viverra nibh libero id quam. Quisque sagittis malesuada sapien. Aliquam sit amet diam consectetur, posuere arcu vel, dapibus ipsum. Duis purus ante, convallis vitae eleifend quis, viverra eget lectus. Duis quam libero, porta vel aliquet sit amet, fringilla eget odio. Donec non varius dolor, ut luctus eros. In laoreet dapibus euismod. Ut in congue tellus, in porttitor lacus. Donec blandit odio ex, nec hendrerit ipsum fermentum vel. Nulla tincidunt sem quis lorem interdum, at convallis ante aliquam. Donec accumsan orci quis maximus gravida. Aenean sodales aliquam quam non fringilla. Nunc dictum semper lectus, in fringilla sapien posuere eget. Duis hendrerit ligula sed velit gravida fringilla. Vivamus rhoncus eu lacus ut ullamcorper. Maecenas imperdiet tristique elit et tincidunt. Etiam quis malesuada arcu. Vivamus id volutpat libero. Donec in pharetra dui. Nam cursus condimentum ligula, nec sodales dui. Curabitur lacus massa, consectetur quis erat lobortis, lobortis consequat magna. Donec et posuere sapien, pharetra sagittis mi. Cras et ligula est. Phasellus id dui sem. Proin commodo ut turpis tristique porta. Morbi posuere tincidunt placerat. Donec at suscipit dolor. Donec elementum at sapien nec elementum. Proin diam metus, mollis a tellus eget, hendrerit fringilla est. Praesent id risus vel nisl egestas varius. Integer commodo ex eros, eu elementum lorem laoreet sed. Aenean eget libero ullamcorper, auctor tellus vel, eleifend ante. Phasellus sollicitudin sapien quis mi facilisis mattis et quis turpis. Aenean hendrerit massa nec convallis cursus. Aliquam sagittis eu libero ut placerat. Nam id lectus eros. Etiam ut lacinia metus, at finibus tortor. Nam tempus, justo porta ultrices tempus, metus dolor vestibulum sapien, a facilisis elit elit iaculis lorem. Donec sodales, ligula in sagittis congue, orci purus imperdiet ipsum, eu bibendum quam lacus nec quam. Curabitur nunc arcu, ultrices sed nisi sit amet, suscipit varius leo. Nullam id accumsan lectus, sit amet eleifend metus. Maecenas pellentesque augue vitae velit bibendum, et faucibus odio volutpat. Donec ullamcorper purus vel odio fermentum, eget posuere risus tincidunt. Suspendisse eget ex vitae elit dictum ullamcorper. Nulla egestas dictum enim et dignissim. Suspendisse potenti. Sed pretium tortor ut felis lobortis, ut elementum nisl suscipit. Aliquam a pharetra magna. Sed ac iaculis nibh. Suspendisse tincidunt mollis accumsan.Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent a faucibus nunc, vitae porta nunc. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Interdum et malesuada fames ac ante ipsum primis in faucibus. Maecenas convallis et mi in faucibus. Aenean sollicitudin sapien massa, vitae molestie felis sagittis vel. Nulla bibendum risus ut metus aliquet efficitur. Donec ex libero, fringilla ac pellentesque non, blandit a dolor. Nam sit amet varius mauris, et blandit elit. Ut hendrerit ut dui vitae pharetra. Ut tincidunt neque vitae ante semper, vel efficitur urna rutrum. Cras in dui posuere erat venenatis tempus et nec augue. Ut scelerisque ex a lacus suscipit mollis. Vestibulum vitae lorem velit. Nam dictum lectus quis consectetur sagittis. Etiam semper, magna quis placerat porta, risus risus accumsan mauris, vel viverra nibh libero id quam. Quisque sagittis malesuada sapien. Aliquam sit amet diam consectetur, posuere arcu vel, dapibus ipsum. Duis purus ante, convallis vitae eleifend quis, viverra eget lectus. Duis quam libero, porta vel aliquet sit amet, fringilla eget odio. Donec non varius dolor, ut luctus eros. In laoreet dapibus euismod. Ut in congue tellus, in porttitor lacus. Donec blandit odio ex, nec hendrerit ipsum fermentum vel. Nulla tincidunt sem quis lorem interdum, at convallis ante aliquam. Donec accumsan orci quis maximus gravida. Aenean sodales aliquam quam non fringilla. Nunc dictum semper lectus, in fringilla sapien posuere eget. Duis hendrerit ligula sed velit gravida fringilla. Vivamus rhoncus eu lacus ut ullamcorper. Maecenas imperdiet tristique elit et tincidunt. Etiam quis malesuada arcu. Vivamus id volutpat libero. Donec in pharetra dui. Nam cursus condimentum ligula, nec sodales dui. Curabitur lacus massa, consectetur quis erat lobortis, lobortis consequat magna. Donec et posuere sapien, pharetra sagittis mi. Cras et ligula est. Phasellus id dui sem. Proin commodo ut turpis tristique porta. Morbi posuere tincidunt placerat. Donec at suscipit dolor. Donec elementum at sapien nec elementum. Proin diam metus, mollis a tellus eget, hendrerit fringilla est. Praesent id risus vel nisl egestas varius. Integer commodo ex eros, eu elementum lorem laoreet sed. Aenean eget libero ullamcorper, auctor tellus vel, eleifend ante. Phasellus sollicitudin sapien quis mi facilisis mattis et quis turpis. Aenean hendrerit massa nec convallis cursus. Aliquam sagittis eu libero ut placerat. Nam id lectus eros. Etiam ut lacinia metus, at finibus tortor. Nam tempus, justo porta ultrices tempus, metus dolor vestibulum sapien, a facilisis elit elit iaculis lorem. Donec sodales, ligula in sagittis congue, orci purus imperdiet ipsum, eu bibendum quam lacus nec quam. Curabitur nunc arcu, ultrices sed nisi sit amet, suscipit varius leo. Nullam id accumsan lectus, sit amet eleifend metus. Maecenas pellentesque augue vitae velit bibendum, et faucibus odio volutpat. Donec ullamcorper purus vel odio fermentum, eget posuere risus tincidunt. Suspendisse eget ex vitae elit dictum ullamcorper. Nulla egestas dictum enim et dignissim. Suspendisse potenti. Sed pretium tortor ut felis lobortis, ut elementum nisl suscipit. Aliquam a pharetra magna. Sed ac iaculis nibh. Suspendisse tincidunt mollis accumsan.Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent a faucibus nunc, vitae porta nunc. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Interdum et malesuada fames ac ante ipsum primis in faucibus. Maecenas convallis et mi in faucibus. Aenean sollicitudin sapien massa, vitae molestie felis sagittis vel. Nulla bibendum risus ut metus aliquet efficitur. Donec ex libero, fringilla ac pellentesque non, blandit a dolor. Nam sit amet varius mauris, et blandit elit. Ut hendrerit ut dui vitae pharetra. Ut tincidunt neque vitae ante semper, vel efficitur urna rutrum. Cras in dui posuere erat venenatis tempus et nec augue. Ut scelerisque ex a lacus suscipit mollis. Vestibulum vitae lorem velit. Nam dictum lectus quis consectetur sagittis. Etiam semper, magna quis placerat porta, risus risus accumsan mauris, vel viverra nibh libero id quam. Quisque sagittis malesuada sapien. Aliquam sit amet diam consectetur, posuere arcu vel, dapibus ipsum. Duis purus ante, convallis vitae eleifend quis, viverra eget lectus. Duis quam libero, porta vel aliquet sit amet, fringilla eget odio. Donec non varius dolor, ut luctus eros. In laoreet dapibus euismod. Ut in congue tellus, in porttitor lacus. Donec blandit odio ex, nec hendrerit ipsum fermentum vel. Nulla tincidunt sem quis lorem interdum, at convallis ante aliquam. Donec accumsan orci quis maximus gravida. Aenean sodales aliquam quam non fringilla. Nunc dictum semper lectus, in fringilla sapien posuere eget. Duis hendrerit ligula sed velit gravida fringilla. Vivamus rhoncus eu lacus ut ullamcorper. Maecenas imperdiet tristique elit et tincidunt. Etiam quis malesuada arcu. Vivamus id volutpat libero. Donec in pharetra dui. Nam cursus condimentum ligula, nec sodales dui. Curabitur lacus massa, consectetur quis erat lobortis, lobortis consequat magna. Donec et posuere sapien, pharetra sagittis mi. Cras et ligula est. Phasellus id dui sem. Proin commodo ut turpis tristique porta. Morbi posuere tincidunt placerat. Donec at suscipit dolor. Donec elementum at sapien nec elementum. Proin diam metus, mollis a tellus eget, hendrerit fringilla est. Praesent id risus vel nisl egestas varius. Integer commodo ex eros, eu elementum lorem laoreet sed. Aenean eget libero ullamcorper, auctor tellus vel, eleifend ante. Phasellus sollicitudin sapien quis mi facilisis mattis et quis turpis. Aenean hendrerit massa nec convallis cursus. Aliquam sagittis eu libero ut placerat. Nam id lectus eros. Etiam ut lacinia metus, at finibus tortor. Nam tempus, justo porta ultrices tempus, metus dolor vestibulum sapien, a facilisis elit elit iaculis lorem. Donec sodales, ligula in sagittis congue, orci purus imperdiet ipsum, eu bibendum quam lacus nec quam. Curabitur nunc arcu, ultrices sed nisi sit amet, suscipit varius leo. Nullam id accumsan lectus, sit amet eleifend metus. Maecenas pellentesque augue vitae velit bibendum, et faucibus odio volutpat. Donec ullamcorper purus vel odio fermentum, eget posuere risus tincidunt. Suspendisse eget ex vitae elit dictum ullamcorper. Nulla egestas dictum enim et dignissim. Suspendisse potenti. Sed pretium tortor ut felis lobortis, ut elementum nisl suscipit. Aliquam a pharetra magna. Sed ac iaculis nibh. Suspendisse tincidunt mollis accumsan.',
};
export default Vue.extend({
  name: 'post-view',
  data() {
    return {
      post,
      data,
    };
  },
});
</script>

<style scoped>
.title-container {
  display: flex;
}
</style>
