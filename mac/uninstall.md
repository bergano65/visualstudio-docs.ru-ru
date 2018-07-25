---
title: Удаление Visual Studio для Mac
description: Инструкции по удалению системы Visual Studio для Mac и связанных с ней инструментов.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.openlocfilehash: dcd305cd7cb3759483c79b75629a688d852f7c7a
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433212"
---
# <a name="uninstalling-visual-studio-for-mac"></a>Удаление Visual Studio для Mac

Существует несколько продуктов Xamarin, обеспечивающих разработку кроссплатформенных приложений, включая автономные приложения, такие как Visual Studio для Mac.

Используйте это руководство для удаления индивидуальных продуктов, перейдя в соответствующий раздел, или воспользуйтесь скриптами, приведенными в разделе [Скрипт удаления](#uninstall-script), чтобы удалить все.

Если ранее вы установили Xamarin Studio на компьютере, в дополнение к описанным ниже действиям может потребоваться выполнить указания из руководства по [удалению Xamarin](https://docs.microsoft.com/xamarin/cross-platform/get-started/installation/uninstalling-xamarin#uninstall-xamarin-studio-on-mac).

## <a name="uninstall-script"></a>Скрипт удаления

Существует два скрипта, которые можно использовать для удаления Visual Studio для Mac и всех компонентов на своем компьютере:

- [Скрипт Visual Studio и Xamarin](#visual-studio-for-mac-and-xamarin-script)
- [Скрипт .NET Core](#net-core-script)

Следующие разделы содержат сведения о скачивании и использовании этих скриптов.

### <a name="visual-studio-for-mac-and-xamarin-script"></a>Скрипт Visual Studio для Mac и Xamarin

Вы можете удалить компоненты Visual Studio и Xamarin за один раз с помощью [скрипта удаления](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh).

Этот скрипт содержит основную часть команд, приведенных в этой статье. Вследствие возможных внешних зависимостей в этом скрипте опущено два аспекта:

- **Удаление Mono**
- **Удаление Android AVD**

Чтобы запустить скрипт, выполните следующее.

1. Щелкните скрипт правой кнопкой мыши и выберите пункт **Сохранить как...**, чтобы сохранить файл на Mac.
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

### <a name="net-core-script"></a>Скрипт .NET Core

Скрипт удаления для .NET Core находится в [репозитории dotnet CLI](https://raw.githubusercontent.com/dotnet/cli/master/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh)

Чтобы запустить скрипт, выполните следующее.

1. Щелкните скрипт правой кнопкой мыши и выберите пункт **Сохранить как...**, чтобы сохранить файл на Mac.
2. Откройте терминал и измените рабочий каталог на папку, куда был скачан скрипт:

    ```bash
    $ cd /location/of/file
    ```
3. Сделайте скрипт исполняемым и запустите его с помощью **sudo**:

    ```bash
    $ chmod +x ./dotnet-uninstall-pkgs.sh
    $ sudo ./dotnet-uninstall-pkgs.sh
    ```
4. Наконец, удалите скрипт удаления .NET Core.

## <a name="uninstall-visual-studio-for-mac"></a>Удаление Visual Studio для Mac

Первый шаг при удалении Visual Studio с Mac заключается в поиске файла **Visual Studio.app** в каталоге **/Applications** и перетаскивании его в **корзину**. Можно также щелкнуть правой кнопкой мыши и выбрать пункт **Переместить в удаленные**, как показано на следующем рисунке:

![Перемещение приложения Visual Studio в корзину](media/uninstall-image1.png)

Удаление этого набора приложений приводит к удалению Visual Studio для Mac, даже если в файловой системе остались другие файлы, связанные с Xamarin.

Чтобы удалить все следы Visual Studio для Mac, нужно выполнить в терминале следующие команды:

```bash
sudo rm -rf "/Applications/Visual Studio.app"
rm -rf ~/Library/Caches/VisualStudio
rm -rf ~/Library/Preferences/VisualStudio
rm -rf ~/Library/Preferences/Visual\ Studio
rm -rf ~/Library/Logs/VisualStudio
rm -rf ~/Library/VisualStudio
rm -rf ~/Library/Preferences/Xamarin/
rm -rf ~/Library/Developer/Xamarin
rm -rf ~/Library/Application\ Support/VisualStudio
rm -rf ~/Library/Application\ Support/VisualStudio/7.0/LocalInstall/Addins/
```

## <a name="uninstall-mono-sdk-mdk"></a>Удаление Mono SDK (MDK)

Mono представляет собой реализацию .NET Framework Майкрософт с открытым исходным кодом и используется всеми продуктами Xamarin (Xamarin.iOS, Xamarin.Android и Xamarin.Mac), чтобы обеспечить разработку на C# в рамках этих платформ.

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

Удалить продукт Xamarin.Mac и его лицензию с компьютера Mac можно с помощью двух соответствующих команд:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Удаление Workbooks и Inspector

Начиная с версии 1.2.2, Xamarin Workbooks и Inspector можно удалить из терминала с помощью следующей команды:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

В более старых версиях требуется вручную удалить следующие артефакты:

* Приложение Workbooks в `"/Applications/Xamarin Workbooks.app"`
* Приложение Inspector в `"Applications/Xamarin Inspector.app"`
* Надстройки `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` и `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Inspector и вспомогательные файлы `/Library/Frameworks/Xamarin.Interactive.framework` и `/Library/Frameworks/Xamarin.Inspector.framework`

## <a name="uninstall-the-xamarin-profiler"></a>Удаление Xamarin Profiler

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
