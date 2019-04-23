---
title: Регистрация обработчиков команд сборки взаимодействия | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a129e0a66399da1efe9bff4d7aef1a94602fa79
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664470"
---
# <a name="registering-interop-assembly-command-handlers"></a>Регистрация обработчиков команд сборки взаимодействия
Необходимо зарегистрировать VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] таким образом, чтобы интегрированной среде разработки (IDE) правильно направляет его команды.

 Можно обновить реестр путем редактирования вручную или с помощью файла регистратора (RGS). Для получения дополнительной информации см. [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Managed Package Framework (MPF) предоставляет следующие функциональные возможности через <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> класса.

- [Команда справочнике по формату таблицы](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) ресурсы находятся в неуправляемых вспомогательные библиотеки DLL пользовательского интерфейса.

## <a name="command-handler-registration-of-a-vspackage"></a>Регистрация обработчика команды пакета VSPackage
 Пакет VSPackage, выступающий в качестве обработчика для пользовательского интерфейса (UI) — на основе команды требуется запись реестра с именем VSPackage `GUID`. Этот параметр реестра указывает расположение файла ресурсов пользовательского интерфейса в пакете VSPackage и ресурса меню в этом файле. Саму запись реестра находится в папке HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<версии >* \Menus, где  *\<версии >* — Это версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], например 9.0.

> [!NOTE]
>  Путь к корневому каталогу HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<версии >* может быть переопределено с помощью альтернативного root при [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] инициализации оболочки. Дополнительные сведения о корневой путь, см. в разделе [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Запись реестра CTMENU ресурсов
 Структура записи реестра выглядит так:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*Идентификатор GUID*> является `GUID` пакета VSPackage в форме {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.

 *\<Сведения о ресурсах >* состоит из трех элементов, разделенных запятыми. Относятся следующие элементы в порядке.

 \<*Путь к DLL ресурсов*>, \< *идентификатор ресурса меню*>, \< *версии меню*>

 В следующей таблице описаны поля \< *сведения о ресурсах*>.

| Элемент | Описание |
|---------------------------| - |
| \<*Путь к DLL ресурсов*> | Это полный путь к DLL, которая содержит ресурс меню ресурса или указан, означающее, что в пакете VSPackage ресурс библиотеки DLL для использования (как указано в подразделе пакетов, где сам пакет VSPackage зарегистрирован).<br /><br /> Обычно это поле оставить пустым. |
| \<*Идентификатор ресурса меню*> | Это идентификатор ресурса `CTMENU` ресурс, содержащий все элементы пользовательского интерфейса для VSPackage, скомпилированной на основе [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) файла. |
| \<*Версия меню*> | Это число, используемое в качестве версии для `CTMENU` ресурсов. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Это значение используется для определения, ему следует произвести повторное слияние содержимого `CTMENU` ресурсов с помощью своего кэша всех `CTMENU` ресурсы. Произвести повторное слияние инициируется, выполнив команду setup devenv.<br /><br /> Это значение следует изначально задано значение 1 и увеличивается после каждого изменения в `CTMENU` ресурсов и прежде, чем произвести повторное слияние происходит. |

### <a name="example"></a>Пример
 Ниже приведен пример несколько записей ресурсов:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>См. также
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Команды и меню, которые используют сборки взаимодействия](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)