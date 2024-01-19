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

##Pour Android :

Il faut aussi modifier une ligne dans votre application Flutter. Dans le fichier android/app/build.gradle, il faut remplacer la ligne suivante dans le defaultConfig:
```bash
minSdkVersion 24
```
C'est à la ligne 48 dans mon code

##Pour iOS :

:warning: Pour ios, il faut modifier le fichier Podfile. Il faut remplacer la ligne suivante avec la version 13.0
```bash
platform :ios, '13.0'
```

Il faudra changer le podfile en ajoutant ces lignes :
```bash
  post_install do |installer|
    installer.pods_project.targets.each do |target|
      flutter_additional_ios_build_settings(target)
      target.build_configurations.each do |config|
        # Additional configuration options could already be set here

        # BEGINNING OF WHAT YOU SHOULD ADD
        config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] ||= [
          '$(inherited)',

          ## dart: PermissionGroup.camera
          'PERMISSION_CAMERA=1',

          ## dart: PermissionGroup.photos
          'PERMISSION_PHOTOS=1',

          ## dart: [PermissionGroup.location, PermissionGroup.locationAlways, PermissionGroup.locationWhenInUse]
          'PERMISSION_LOCATION=1',

          ## dart: PermissionGroup.sensors
          'PERMISSION_SENSORS=1',

          ## dart: PermissionGroup.bluetooth
          'PERMISSION_BLUETOOTH=1',

          # add additional permission groups if required
        ]
        # END OF WHAT YOU SHOULD ADD
      end
    end
  end
  
```
:warning: Il faut faire attention de ne pas dupliquer le post_install do |installer|, il ne doit y en avoir qu'un seul.

Vous pouvez retrouver cela dans le github du plugin ar_flutter_plugin

Ensuite :
Changer le fichier info.plist dans Xcode :

	Ajouter NSCameraUsageDescription :

		élément : Privacy - Camera usage description

		valeur : Access camera

Pour finir ajouter : https://stackoverflow.com/questions/70657051/app-settings-not-present-in-system-settings-in-ios

Cela consiste à supprimer tous les éléments de Preferences Items de Root.plist

## Utilisation

Il vous suffit ensuite de build l'app sur votre téléphone et de lancer l'application. Si votre téléphone scanne une surface, un repère devrait apparaitre.


