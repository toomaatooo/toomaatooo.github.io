---
layout: blog
title: Dialogue System for Unity usage record
date: 2023-05-12 10:01:35
categories:
  - Skill
  - Unity
tags:
  - Game
  - Dialogue System for unity
  - Unity
---

While creating the recent graduation project, I decided to use the Unity Dialogue System plug-in to implement the dialogue system. I searched for some detailed tutorials on the Internet but couldn't find any. Here are some points that confused me at the time.

# Avatar changes for NPCs

1. Dialogue database for the corresponding dialogue

![dialogue database](image-20230512101741139.png)

2. Change the **avatar of the corresponding NPC** by clicking on it

![更改头像的NPC](image-20230512101802916.png)

3. Just change the **portrait textures** in the inspector panel

![portrait textures](image-20230512101956715.png)

# Conversation UI Changes

1. Change the corresponding **UI prefab**.

2. Communicate with art partners to change the component layout. The figure below is the initial UI panel for the basic dialogue system.
   ![UI prefab](image-20230512102503171.png)
   The UI effect we want is shown in figure.
   ![The desired UI effect](image-20230512102622755.png)
   Communicate with art partners to determine the UI layout, and swap the positions of the NPC and player dialog boxes.

3. Beautify the dialog.

   * NPC part

     * **Basemap replacement.** Change the portrait image's spirit.

       ![portrait image](image-20230512103354589.png)

       Need to check the following:

       ![portrait image2](image-20230512110957945.png)

     * **NPC avatar replacement.** Use the method shown above to replace the character's avatar in the database.

     * **NPC and base map replacement.** Because the artist draws a different dialog box for each of the NPCs, select the dialog box and the character vertical drawing to replace it in portrait textures. It's difficult to unify the size in Photoshop, so I can only adjust it slowly.

     * **Change images and typography.** Uncheck the horizontal layout group of the PC subtitle panel.

       ![horizontal layout group](image-20230512111831437.png)

       After adjusting the text and image position, **check again**.

   * Player part

     * Change the spirit of the scroll rect.

       ![scroll rect](image-20230512111622101.png)

       ![scroll rect2](image-20230512111734094.png)

     * Section of writing.

       Change **typography**. It is necessary to uncheck and change the Vertical Layout Group of scroll rect and Response Button Template. Check again after changing.

       Because the text part involves **option distribution**, the arrangement parameters need to be fine-tuned. This is the final effect exhibited by the following parameters.

       ![final effect](image-20230512112922091.png)

       ![the final effect is clearly shown](image-20230512113011077.png)

       The **red boxes** may affect option arrangement:

       ![parameter](image-20230512113040001.png)

       ![parameter2](image-20230512113128552.png)


Finally, I would like to say something that has nothing to do with the article. Good UI really needs to be in harmony with the art again and again... It takes long communication to determine the layer relationship and control the shape of the texture.
