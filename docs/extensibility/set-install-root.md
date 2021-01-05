---
title: Установка вне папки Extensions с помощью VSIX v3 | Документация Майкрософт
description: Узнайте, как установить ресурсы расширения пакета SDK для Visual Studio за пределами папки Extensions и какие расположения являются допустимыми.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 73bfb963122762c3185a964826a11dca5e771717
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716020"
---
# <a name="install-outside-the-extensions-folder"></a>Установка за пределами папки расширений

Начиная с Visual Studio 2017 и VSIX v3 (версия 3), ресурсы расширения можно устанавливать за пределами папки Extensions. Сейчас следующие расположения включены в качестве допустимых расположений установки (где [INSTALLDIR] сопоставлен с каталогом установки экземпляра Visual Studio):

* [INSTALLDIR] \Мсбуилд
* [INSTALLDIR] \Ксмл\счемас
* [INSTALLDIR] \Common7\IDE\PublicAssemblies
* [INSTALLDIR] \Лиценсес
* [INSTALLDIR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDIR] \Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets (поддерживается только для Visual Studio 2017; не рекомендуется для Visual Studio 2019 и более поздних версий)

> [!NOTE]
> Формат VSIX не позволяет устанавливать вне структуры папок установки Visual Studio. 

Для поддержки установки в эти каталоги необходимо установить VSIX-экземпляр для каждого компьютера. Это можно включить, установив флажок "все пользователи" в конструкторе Extension. vsixmanifest:

![Проверка всех пользователей](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Как задать InstallRoot

Чтобы задать каталоги установки, можно использовать окно **Свойства** в Visual Studio. Например, можно задать `InstallRoot` для свойства ссылки проекта одно из указанных выше расположений.

![установка корневых свойств](media/install-root-properties.png)

Это приведет к добавлению некоторых метаданных в соответствующее `ProjectReference` свойство внутри файла CSPROJ проекта VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Файл. csproj можно изменить непосредственно, если предпочитаете.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Как задать вложенный путь в InstallRoot

Если вы хотите установить на вложенный путь под `InstallRoot` , это можно сделать, задав `VsixSubPath` свойство так же, как `InstallRoot` свойство. Например, предположим, что нам нужно, чтобы в качестве выходных данных ссылки на наш проект устанавливался "[INSTALLDIR] \MSBuild\MyCompany\MySDK\1.0". Это можно легко сделать с помощью конструктора свойств:

![задать вложенный путь](media/set-subpath.png)

Соответствующие CSPROJ изменения будут выглядеть следующим образом:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Дополнительные сведения

Изменения конструктора свойств применяются не только к ссылкам на проекты; можно `InstallRoot` также задать метаданные для элементов внутри проекта (используя те же методы, которые описаны выше).
