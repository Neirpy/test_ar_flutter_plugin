# Test AR Plugin

C'est un code test qui utilise le plugin AR de la bibliothèque ar_flutter_plugin :
https://github.com/CariusLars/ar_flutter_plugin

Elle permet de mélanger des éléments de ARCore et de ARKit pour créer une application de réalité augmentée.
Malheureusement, elle n'est plus maintenue et ne fonctionne plus avec les dernières versions de Flutter.

Il faut donc ce repo pour pouvoir l'utiliser :
https://github.com/hlefe/ar_flutter_plugin_flutterflow

Celui-ci est maintenu par un développeur qui a fait une copie du plugin et l'a adapté pour qu'il fonctionne avec les dernières versions de Flutter.

## Installation

Au préalable, il faut installer Flutter sur votre ordinateur. Pour cela, il faut suivre les instructions sur le site officiel :
https://flutter.dev/docs/get-started/install


Pour installer le plugin, il faut taper la commande suivante dans le terminal :
```bash
flutter pub add ar_flutter_plugin_flutterflow
```

Il faut aussi modifier une ligne dans votre application Flutter. Dans le fichier android/app/build.gradle, il faut remplacer la ligne suivante dans le defaultConfig:
```bash
minSdkVersion 24
```
C'est à la ligne 48 dans mon code

## Utilisation

Il vous suffit ensuite de build l'app sur votre téléphone et de lancer l'application. Si votre téléphone scanne une surface, un repère devrait apparaitre.


