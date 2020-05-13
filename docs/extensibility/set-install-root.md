---
title: Установка вне папки расширений с VSIX v3 Документы Майкрософт
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa2c7d97dda9bba139ec613b367eedbc6307848a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700184"
---
# <a name="install-outside-the-extensions-folder"></a>Установка за пределами папки расширений

Начиная с Visual Studio 2017 и VSIX v3 (версия 3), активы расширения могут быть установлены за пределами папки расширений. В настоящее время следующие местоположения включены в качестве действительных местоположений установки (где «INSTALLDIR» отображается в каталоге установки примера Visual Studio):

* «INSTALLDIR»-MSBuild
* «СТАНТДИР»
* «INSTALLDIR»(Общие7-IDE-PublicAssemblies
* Лицензии «INSTALLDIR»
* «INSTALLDIR»(Общие7-IDE-ReferenceAssemblies
* «INSTALLDIR»(Общие7-IDE-RemoteDebugger
* «INSTALLDIR»(Общие7-IDE-VC-VCTargets (поддерживается только для Visual Studio 2017; обезврежено для Visual Studio 2019 и более поздних)

> [!NOTE]
> Формат VSIX не позволяет устанавливать за пределами структуры папок Visual Studio. 

Для того, чтобы поддержать установку в эти каталоги, VSIX должны быть установлены "на экземпляр на машину". Это может быть включено путем проверки "всех пользователей" флажок в extension.vsixmanifest дизайнера:

![проверить всех пользователей](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Как установить InstallRoot

Чтобы установить каталоги установки, можно использовать окно **Properties** в Visual Studio. Например, можно установить свойство `InstallRoot` ссылки проекта на одно из вышеперечисленных мест:

![установить корневые свойства](media/install-root-properties.png)

Это добавит некоторые метаданные `ProjectReference` в соответствующее свойство внутри файла .csproj проекта VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Вы можете отодвигать файл .csproj напрямую, если вы предпочитаете.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Как установить подперенок под InstallRoot

Если вы хотите установить на подперенок `InstallRoot`под, вы можете `VsixSubPath` сделать `InstallRoot` это, установив свойство так же, как свойство. Например, предположим, что мы хотим, чтобы выход нашей справки по проекту был установлен на «INSTALLDIR»MSBuild»MyCompany»MySDK 1.0. Мы можем сделать это легко с дизайнером недвижимости:

![набор подпат](media/set-subpath.png)

Соответствующие изменения .csproj будут выглядеть следующим образом:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Дополнительная информация

Изменения в проекте свойств применяются не только к ссылкам на проекты; метаданные `InstallRoot` можно также установить для элементов внутри проекта (используя те же методы, описанные выше).
