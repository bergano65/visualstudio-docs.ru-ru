---
title: Регистрация Обработчиков командования Межоп ассамблеи (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e2ab6389f1e0d369dd095290d12c97431c44155
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705861"
---
# <a name="registering-interop-assembly-command-handlers"></a>Регистрация обработчиков команд сборки взаимодействия
VSPackage должен зарегистрироваться [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] таким образом, чтобы интегрированная среда разработки (IDE) правильно маршрутизацировала свои команды.

 Реестр может быть обновлен либо с помощью ручного редактирования или с помощью файла Регистратора (.rgs). Для получения дополнительной информации см. [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Рамочная программа управляемого пакета (MPF) предоставляет эту функциональность в <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> классе.

- [Справочные](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) ресурсы командного формата расположены в неуправляемых спутниковых uI dlls.

## <a name="command-handler-registration-of-a-vspackage"></a>Регистрация обработчика команды VSPackage
 VSPackage, выступающий в качестве обработчика для пользовательских команд интерфейса (UI), требует регистрации, названной в честь VSPackage. `GUID` В этой записи реестра указывается местоположение файла ресурсов uI VSPackage и ресурс меню в этом файле. Сама запись реестра находится под HKEY_LOCAL_MACHINE-Software-Microsoft-VisualStudio\\*\<Версия>*«Menus, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]где * \<версия>* является версией, например 9.0.

> [!NOTE]
> Корневой путь HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio\\*\<Version>* может быть переопределен с альтернативным корнем, когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] оболочка инициализирована. Для получения дополнительной информации о корневом пути [см.](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

### <a name="the-ctmenu-resource-registry-entry"></a>Вход в реестр ресурсов CTMENU
 Структура регистрации:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> `GUID` является VSPackage в форме «XXXXXXXX-XXXXXXXX-XXXX-XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX.

 Ресурсная информация>состоит из трех элементов, разделенных запятыми. * \<* Эти элементы, в порядке:

 \<*Путь к> ресурса DLL,* \< *идентификатор ресурсов меню*>, \<Версия *меню*>

 В следующей таблице \<описаны области *информационно-> ресурсов.*

| Элемент | Описание |
|---------------------------| - |
| \<*Путь к ресурсу DLL*> | Это полный путь к ресурсу DLL, который содержит ресурс меню или он остается пустым, указывая, что ресурс DLL VSPackage должен быть использован (как указано в подключке пакетов, где зарегистрирован сам VSPackage).<br /><br /> Принято оставлять это поле пустым. |
| \<*Идентификатор ресурсов меню*> | Это идентификатор `CTMENU` ресурса, содержащий все элементы uI для VSPackage, составленный из файла [.vsct.](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) |
| \<*Версия меню*> | Это число, используемое в `CTMENU` качестве версии для ресурса. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]использует это значение для определения необходимости повторного `CTMENU` слияния содержимого ресурса с кэшем всех `CTMENU` ресурсов. Повторное слияние запускается выполнением команды установки devenv.<br /><br /> Это значение должно быть первоначально установлено до 1 и `CTMENU` приравнено после каждого изменения ресурса и до того, как происходит слияние. |

### <a name="example"></a>Пример
 Вот пример нескольких записей ресурсов:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>См. также
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Команды и меню, которые используют сборки взаимодействия](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
