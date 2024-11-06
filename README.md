Projet réalisé par Erwan Bonafous et Mahammedi Simon
![image](https://github.com/DanmakuGecko/Coolbox-project/assets/72706524/29dd84a9-69ae-4cb2-912a-27ea82950be6)


Lecture vidéo

Afin d'observer les traces et de les lires à travers le programme d'analyse, il etait nécaissaire de lire une source vidéo. Nous dispsions d'une caméra à cable FFC, qui peux être relié a un rasberry pi3. 
Un problème important s'est manifesté quand nous avons réalisé que le rasberry pi3 n'était pas un appareil suffisament puissant pour traiter l'image avec une bonne qualité, nous avons donc décidé de transferer le flux de l'image directement vers un ordinateur portable à proximité.

Transfert via réseau local

A l'aide de ressource sur internet, nous avions essayé de relier le flux vidéo du rasberry à un PC windows, pour se faire, nous avons utilisé Motion, qui est une application couramment utilisée pour des projets de caméra de surveillance accessible partout dans le monde. Nous passons les détails, mais après plusieurs heure de test pour la configuration, nous n'avons pas reussi à ouvrir les ports réseaux de notre box internet. De plus, nous avons réalisé que l'usage du réseau local rendrais notre projet unitilisable en dehors du domicile où nous avions réalisé les test.
Transfert du flux vidéo via VLC

D'abord, nous avons utilisé une fonction très pratique du lecteur VLC pour lire le flux vidéo depuis une page web, d'adresse : http://192.168.1.103:40000/ (par exemple) contenant l'adresse ip locale du rasberry, ainsi que le port 40000 que nous avons ouvert  sur la box internet.

Dès lors, mettre ce liens sur un navigateur nous permet de télécharger en direct un fichier vidéo.
Mettre ce liens sur VLC nous permet d'afficher directement la vidéo, avec une latence plutôt élevée malheureusement. Mais la fréquence d'affichage et la qualité étant bonne, nous nous contenterons de cette méthode. 
raspivid -t 999999 -w 640 -h 480 -fps 30 -b 1000000 -o - | cvlc -vvv stream:///dev/stdin --sout '#standard{access=http,mux=ts,dst=:40000}' :demux=h264
commande lancement flux vidéo sur le port 40000 : a lancer sur l'invité de commande de linux

Le programme utilisé pour la capture vidéo est contenu dans le programme python 'picamera.py'


![image](https://github.com/DanmakuGecko/Coolbox-project/assets/72706524/91384130-90cb-4475-8432-1294ed07d8eb)





![image](https://github.com/DanmakuGecko/Coolbox-project/assets/72706524/25e6c595-e89a-40a9-baf9-526e13c4c249)
![image](https://github.com/DanmakuGecko/Coolbox-project/assets/72706524/ab04a3ae-6a80-40e1-a45f-32a3cac1db02)

