<template>
  <Page>
    <ActionBar title="Pueblo Duerme" class="action-bar" />
    <TabView height="100%" androidTabsPosition="bottom">
      <TabViewItem title="Añadir">
        <ScrollView>
          <StackLayout class="home-panel">
            <Player @add="AddToList"></Player>
          </StackLayout>
        </ScrollView>
      </TabViewItem>

      <TabViewItem title="Jugadores">
        <ScrollView>
          <ListView
            @itemTap="onDeleteTap"
            v-for="player in listPlayer"
            :key="player"
          >
            <v-template>
              <Label :text="player" textWrap=" true " />
            </v-template>
          </ListView>
        </ScrollView>
      </TabViewItem>

      <TabViewItem title="Roles">
        <ScrollView>
          <ListView @itemTap="tapRole" v-for="rol in roles">
            <v-template>
              <Label :text="rol.label" />
            </v-template>
            <FlexboxLayout
              flexDirection="column"
              justifyContent="center"
              alignItems="center"
            >
              <Label :text="rol.label" />
              <Switch :checked="rol.active" />
            </FlexboxLayout>
            <!-- <Switch :checked="rol.active" /> -->
          </ListView>
        </ScrollView>
      </TabViewItem>

      <TabViewItem title="Partida">
        <ScrollView> </ScrollView>
      </TabViewItem>
    </TabView>
  </Page>
</template>

<script>
import Player from './Player';
export default {
  components: {
    Player,
  },
  data() {
    return {
      listPlayer: [],
      roles: [
        {
          id: 0,
          label: 'Bufon',
        },
        {
          id: 1,
          label: 'Guardaespaldas',
        },
        {
          id: 2,
          label: 'Cupido',
        },
        {
          id: 3,
          label: 'Asesino',
          active: true,
        },
        {
          id: 4,
          label: 'Complice',
        },
        {
          id: 5,
          label: 'Bruja',
        },
        {
          id: 6,
          label: 'Videnten',
        },
        {
          id: 7,
          label: 'Panadero',
        },
        {
          id: 8,
          label: 'Justiciero',
        },
      ],
    };
  },
  methods: {
    AddToList(event) {
      console.log(' Hemos detectado el evento ');
      this.listPlayer.unshift(event);
    },
    onDeleteTap: function (args) {
      confirm({
        title: 'Eliminando',
        message: 'Seguro que quieres eliminarlo',
        okButtonText: 'Eliminar',
        cancelButtonText: 'Cancelar',
      }).then((result) => {
        if (result) this.listPlayer.splice(args.index, 1);
      });
    },
    tapRole(args) {
      console.log(args.item);
      const id = args.item.id;

      this.roles.forEach((rol) => {
        if (rol.id == id) {
          if ('active' in rol && rol.active === undefined) rol.active = false;
          rol.active = !rol.active;
        }
      });
    },
  },
};
</script>

<style scoped>
.home-panel {
  vertical-align: center;
  font-size: 20;
  margin: 15;
}

.description-label {
  margin-bottom: 15;
}
</style>
