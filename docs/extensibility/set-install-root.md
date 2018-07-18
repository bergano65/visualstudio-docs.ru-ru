---
title: Установка в папке расширений с VSIX v3 | Документы Microsoft
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8476b300974d66efc60f647c897ec6892191e7fa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136787"
---
# <a name="installing-outside-the-extensions-folder"></a>Установка в папке расширений

Начиная с Visual Studio 2017 г. и VSIX v3 (версия 3), теперь поддерживается установка средств расширения вне папки расширения. В настоящее время нижеперечисленных включены в качестве расположения установки (где сопоставленного [INSTALLDIR] каталог установки экземпляр Visual Studio):

* \MSBuild [INSTALLDIR]
* [INSTALLDIR] \Xml\Schemas
* \Common7\IDE\PublicAssemblies [INSTALLDIR]
* \Licenses [INSTALLDIR]
* \Common7\IDE\ReferenceAssemblies [INSTALLDIR]
* \Common7\IDE\RemoteDebugger [INSTALLDIR]
* \Common7\IDE\VC\VCTargets [INSTALLDIR]

>**Примечание:** формата VSIX не позволяют установить вне структуру папок для установки VS.

Чтобы обеспечить поддержку установки для этих каталогов, VSIX необходимо установить «для каждого экземпляра на компьютере». Эту возможность можно включить, установив флажок «все пользователи» в конструкторе extension.vsixmanifest:

![Проверьте все пользователи](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Как задать Корневого_каталога_установки

Чтобы установить нужные каталоги установки, можно использовать **свойства** в Visual Studio. Например, можно задать `InstallRoot` свойство ссылку на проект в одно из вышеуказанных местах:

![Установка свойств корневого](media/install-root-properties.png)

Это добавит некоторые метаданные в соответствующий `ProjectReference` свойства внутри проекта VSIX CSPROJ-файл:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Примечание:** CSPROJ-файл можно редактировать напрямую, если вы предпочитаете.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Как задать вложенным корневого_каталога_установки

Если вы хотите установить к вложенным под `InstallRoot`, это можно сделать, задав `VsixSubPath` свойства так же, как `InstallRoot` свойство. Предположим, мы хотим, чтобы наши ссылки проекта выходные данные для установки "[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0". Мы это легко сделать с помощью свойства конструктора:

![вложенным набором](media/set-subpath.png)

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

Свойство конструктора изменения применяются не только ссылки на проект; можно задать `InstallRoot` метаданные элементов в проекте, а также (используя те же методы, описанные выше).
