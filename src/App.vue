<template>
  <ion-app>

    <ion-header>
      <ion-grid>
        <ion-row>
          <ion-col>
            <div id="supergraphic"></div>
          </ion-col>
        </ion-row>

        <ion-row>
          <ion-col>
            <div id="slogan"></div>
          </ion-col>
        </ion-row>
      </ion-grid>
    </ion-header>
  

    <ion-content>
      <div id="content">
      
        <ion-label> asdjasdas</ion-label>
      
      </div>
    </ion-content>
    
  </ion-app>
</template>

<script lang="ts">
import { IonApp, IonContent, IonIcon, IonItem, IonLabel, IonList, IonListHeader, IonMenu, IonMenuToggle, IonNote, IonRouterOutlet, IonSplitPane } from '@ionic/vue';
import { defineComponent, ref } from 'vue';
import { useRoute } from 'vue-router';
import { archiveOutline, archiveSharp, bookmarkOutline, bookmarkSharp, heartOutline, heartSharp, mailOutline, mailSharp, paperPlaneOutline, paperPlaneSharp, trashOutline, trashSharp, warningOutline, warningSharp } from 'ionicons/icons';

export default defineComponent({
  name: 'App',
  components: {
    IonApp, 

  },
  setup() {
    const selectedIndex = ref(0);
    const appPages = [
      {
        title: 'Inbox',
        url: '/folder/Inbox',
        iosIcon: mailOutline,
        mdIcon: mailSharp
      },
      {
        title: 'Outbox',
        url: '/folder/Outbox',
        iosIcon: paperPlaneOutline,
        mdIcon: paperPlaneSharp
      },
      {
        title: 'Favorites',
        url: '/folder/Favorites',
        iosIcon: heartOutline,
        mdIcon: heartSharp
      },
      {
        title: 'Archived',
        url: '/folder/Archived',
        iosIcon: archiveOutline,
        mdIcon: archiveSharp
      },
      {
        title: 'Trash',
        url: '/folder/Trash',
        iosIcon: trashOutline,
        mdIcon: trashSharp
      },
      {
        title: 'Spam',
        url: '/folder/Spam',
        iosIcon: warningOutline,
        mdIcon: warningSharp
      }
    ];
    const labels = ['Family', 'Friends', 'Notes', 'Work', 'Travel', 'Reminders'];
    
    const path = window.location.pathname.split('folder/')[1];
    if (path !== undefined) {
      selectedIndex.value = appPages.findIndex(page => page.title.toLowerCase() === path.toLowerCase());
    }
    
    const route = useRoute();
    
    return { 
      selectedIndex,
      appPages, 
      labels,
      archiveOutline, 
      archiveSharp, 
      bookmarkOutline, 
      bookmarkSharp, 
      heartOutline, 
      heartSharp, 
      mailOutline, 
      mailSharp, 
      paperPlaneOutline, 
      paperPlaneSharp, 
      trashOutline, 
      trashSharp, 
      warningOutline, 
      warningSharp,
      isSelected: (url: string) => url === route.path ? 'selected' : ''
    }
  }
});
</script>

<style scoped>

*{
  padding: 0px;
  margin: 0px;
}

#supergraphic{
  background-image: url("../public/assets/supergraphic.svg");
  background-size: cover;
  height: 10px;
  background-repeat: no-repeat;
}

#slogan{
  background-image: url("../public/assets/slogan.png");
  background-size: contain; 
  height: 70px;
  background-repeat: no-repeat;

}

#content{
  display: flex;
  justify-content: center;
}

</style>
