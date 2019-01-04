---
title: Установка за пределами папки расширений с помощью VSIX v3 | Документация Майкрософт
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 847ce9bc55e93f292ffdfe6f237e8c39eeac9fd4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968502"
---
# <a name="installing-outside-the-extensions-folder"></a>Установка за пределами папки расширений

Начиная с Visual Studio 2017 и VSIX v3 (версия 3), теперь поддерживаются для установки расширения ресурсов за пределами папки расширений. В настоящее время как расположения правильность установки (где сопоставленного [INSTALLDIR] каталог установки экземпляра Visual Studio) включены следующие расположения:

* \MSBuild [INSTALLDIR]
* [INSTALLDIR] \Xml\Schemas
* \Common7\IDE\PublicAssemblies [INSTALLDIR]
* \Licenses [INSTALLDIR]
* \Common7\IDE\ReferenceAssemblies [INSTALLDIR]
* \Common7\IDE\RemoteDebugger [INSTALLDIR]
* \Common7\IDE\VC\VCTargets [INSTALLDIR]

>**Примечание.** Формат VSIX не позволяют установить за пределами структуры папок установки VS.

Для поддерживают установку на эти каталоги, VSIX необходимо установить «для каждого экземпляра на уровне компьютера». Эту функцию можно включить, установив флажок «все пользователи» в конструкторе extension.vsixmanifest:

![Проверьте все пользователи](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Как задать InstallRoot

Чтобы установить нужные каталоги установки, можно использовать **свойства** окно в Visual Studio. Например, можно задать `InstallRoot` свойства ссылок на один из вышеуказанных местах:

![установить свойства корневого ресурса](media/install-root-properties.png)

Это добавит некоторые метаданные в соответствующий `ProjectReference` свойства внутри проекта VSIX CSPROJ-файл:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Примечание.** Можно изменить CSPROJ-файл напрямую, если вы предпочитаете.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Как задать вложенный путь в разделе InstallRoot

Если вы хотите установить субконтуру под `InstallRoot`, это можно сделать, задав `VsixSubPath` свойства так же, как `InstallRoot` свойство. Например, предположим, мы хотим, чтобы выходные данные нашей ссылку на проект для установки "[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0". Мы это можно легко сделать с помощью свойства конструктора:

![вложенный путь набора](media/set-subpath.png)

Соответствующие изменения CSPROJ-файл будет выглядеть следующим образом:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Дополнительные сведения

Применить изменения свойств конструктора больше, чем просто перекрестные ссылки между проектами; можно задать `InstallRoot` метаданные элементов в проекте, а также (используя те же методы, описанные выше).
