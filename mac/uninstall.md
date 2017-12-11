---
title: "Удаление Visual Studio для Mac | Документы Майкрософт"
description: "Инструкции по удалению системы Visual Studio для Mac и связанных с ней инструментов."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.openlocfilehash: f1e94d08addc4045bfda9ffa34b77755a0a54a89
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="uninstalling-visual-studio-for-mac"></a>Удаление Visual Studio для Mac

Существует несколько продуктов Xamarin, обеспечивающих разработку кроссплатформенных приложений, включая автономные приложения, такие как Visual Studio для Mac.

Это руководство можно использовать при раздельном удалении продуктов, перейдя в соответствующий раздел. Чтобы удалить весь набор инструментов Xamarin, выполните все руководство от начала и до конца.

Если ранее вы установили Xamarin Studio на компьютере, в дополнение к описанным ниже действиям может потребоваться выполнить указания из руководства по [удалению](https://developer.xamarin.com/guides/cross-platform/getting_started/installation/uninstalling_xamarin/) на сайте developer.xamarin.com.

## <a name="uninstall-script"></a>Скрипт удаления

Вы можете удалить систему Visual Studio и связанных с ней компоненты за один раз с помощью скрипта удаления, расположенного [здесь](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh).

Этот скрипт содержит основную часть команд, приведенных в этой статье. Вследствие возможных внешних зависимостей в этом скрипте опущено два аспекта:

- **Удаление Mono**
- **Удаление Android AVD**

Чтобы запустить скрипт, выполните следующее:

1. Щелкните скрипт правой кнопкой мыши и выберите пункт **Сохранить как**, чтобы сохранить файл на Mac.
2. Откройте терминал и измените рабочий каталог на папку, куда был скачан скрипт:

    ```bash
    $ cd /location/of/file
    ```
3. Сделайте скрипт исполняемым и запустите его с помощью **sudo**:

    ```bash
    $ chmod +x ./uninstall-vsmac.sh
    $ sudo ./uninstall-vsmac.sh
    ```
4. Наконец, удалите этот скрипт удаления.

## <a name="uninstall-visual-studio-for-mac"></a>Удаление Visual Studio для Mac

Первый шаг при удалении Visual Studio с Mac заключается в поиске файла **Visual Studio.app** в каталоге **/Applications** и перетаскивании его в **корзину**. Можно также щелкнуть правой кнопкой мыши и выбрать пункт **Переместить в удаленные**, как показано ниже:

![Перемещение приложения Visual Studio в корзину](media/uninstall-image1.png)

Удаление этого набора приложений приведет к удалению Visual Studio для Mac, даже если в файловой системе остались другие файлы, связанные с Xamarin.

Чтобы удалить все следы Visual Studio для Mac, нужно выполнить в терминале следующие команды:

```bash
sudo rm -rf "/Applications/Visual Studio.app"
rm -rf ~/Library/Caches/VisualStudio
rm -rf ~/Library/Preferences/VisualStudio
rm -rf "~/Library/Preferences/Visual Studio"
rm -rf ~/Library/Logs/VisualStudio
rm -rf ~/Library/VisualStudio
rm -rf ~/Library/Preferences/Xamarin/
rm -rf ~/Library/Developer/Xamarin
```

## <a name="uninstall-mono-sdk-mdk"></a>Удаление Mono SDK (MDK)

Mono представляет собой реализацию .NET Framework Майкрософт с открытым исходным кодом и используется всеми продуктами Xamarin — Xamarin.iOS, Xamarin.Android и Xamarin.Mac, чтобы обеспечить разработку на C# в рамках этих платформ.

> [!WARNING]
> Существуют и другие приложения, не входящие в Visual Studio для Mac, которые используют Mono, например Unity.
> Перед удалением Mono убедитесь в отсутствии зависимостей от нее.

Чтобы удалить платформу Mono с компьютера, выполните следующие команды в терминале:

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Удаление Xamarin.Android

Существует несколько элементов, необходимых для установки и использования Xamarin.Android, таких как пакет SDK для Android и пакет SDK для Java.

Для удаления Xamarin.Android используйте следующие команды:

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Удаление пакета SDK для Android и пакета SDK для Java

Пакет SDK для Android требуется для разработки приложений Android. Чтобы полностью удалить все части пакета SDK для Android, найдите файл в папке **~/Library/Developer/Xamarin/** и переместите его в **корзину**.

Пакет SDK для Java (JDK) не требуется удалять, так как он уже входит в состав Mac OS X и macOS.

### <a name="uninstall-android-avd"></a>Удаление Android AVD

> [!WARNING]
> Существуют и другие приложения, не входящие в Visual Studio для Mac, которые используют Android AVD и указанные дополнительные компоненты Android, например Android Studio.
> Удаление этого каталога может привести к нарушению работы проектов в Android Studio. 

Для удаления Android AVD и дополнительных компонентов Android используйте следующую команду:

```bash
rm -rf ~/.android
```

Для удаления только Android AVD используйте следующую команду:

```bash
rm -rf ~/.android/avd
```

 

## <a name="uninstall-xamarinios"></a>Удаление Xamarin.iOS

Xamarin.iOS позволяет разрабатывать приложения iOS на языках C# и F # в Visual Studio для Mac.

Узел сборки Xamarin также автоматически устанавливался вместе с более ранними версиями Xamarin.iOS, чтобы обеспечить разработку приложений iOS в Visual Studio. Чтобы удалить оба этих компонента с компьютера, сделайте следующее:

Выполните следующие команды в терминале для удаления всех файлов Xamarin.iOS из файловой системы:

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Удаление Xamarin.Mac

После успешного удаления Visual Studio для Mac можно удалить продукт Xamarin.Mac и его лицензию с помощью двух следующих команд:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Удаление Workbooks и Inspector

Начиная с версии 1.2.2, Xamarin Workbooks и Inspector можно удалить из терминала с помощью следующей команды:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

В более старых версиях требуется вручную удалить следующие компоненты:

* Приложение Workbooks в `"/Applications/Xamarin Workbooks.app"`
* Приложение Inspector в `"Applications/Xamarin Inspector.app"`
* Надстройки `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` и `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Inspector и вспомогательные файлы `/Library/Frameworks/Xamarin.Interactive.framework` и `/Library/Frameworks/Xamarin.Inspector.framework`

# <a name="uninstall-the-xamarin-profiler"></a>Удаление Xamarin Profiler

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Удаление установщика Visual Studio

Чтобы удалить все следы универсального установщика Xamarin, используйте следующие команды:

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```
