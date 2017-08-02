---
title: "Установка вне папки расширения с VSIX v3 | Документы Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 6d87c86d0a7793f661c6a3b28e95340f3a28c616
ms.lasthandoff: 03/07/2017

---
# <a name="installing-outside-the-extensions-folder"></a>Установка вне папки расширения

Начиная с Visual Studio 2017 г. и VSIX v3 (версия 3), существует поддержка теперь установка средств расширения вне папки расширения. В настоящее время как расположения установки (где сопоставленного [installdir] каталог установки экземпляра Visual Studio) включены следующие расположения:

* \Common7\IDE\PublicAssemblies [installdir]
* \Common7\IDE\ReferenceAssemblies [installdir]
* \MSBuild [installdir]
* \Schemas [installdir]
* \Licenses [installdir]
* \RemoteDebugger [installdir]
* \VSTargets [installdir]

>**Примечание:** формата VSIX не позволяют устанавливать вне структуры папки установки VS.

Для поддержки установки для этих каталогов, VSIX должен устанавливаться «каждого экземпляра каждого компьютера». Эту возможность можно включить, установив флажок «все пользователи» в конструкторе extension.vsixmanifest:

![Проверка всех пользователей](~/extensibility/media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Как задать Корневого_каталога_установки

Чтобы установить нужные каталоги установки, можно использовать **свойства** в Visual Studio. Например, можно задать `InstallRoot` свойства ссылку на проект в одно из вышеуказанных местах:

![Установка свойств корневого](~/extensibility/media/install-root-properties.png)

Это добавит некоторые метаданные к соответствующим `ProjectReference` свойства внутри проекта VSIX CSPROJ-файл:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Примечание:** вы можете изменить CSPROJ-файл напрямую, если вы предпочитаете.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Как задать вложенный корневого_каталога_установки

Если вы хотите установить к вложенным под `InstallRoot`, это можно сделать, задав `VsixSubPath` как свойство `InstallRoot` свойство. Предположим, мы хотим выходной нашего проекта ссылка для установки "[installdir]\MSBuild\MyCompany\MySDK\1.0". Мы это легко сделать с помощью свойства конструктора:

![вложенным набором](~/extensibility/media/set-subpath.png)

Соответствующие изменения .csproj будет выглядеть следующим образом:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Дополнительные сведения

Применить изменения свойств конструктора больше, чем просто ссылки проекта; можно задать `InstallRoot` метаданные для элементов внутри проекта, а также (используя те же методы, описанные выше).

