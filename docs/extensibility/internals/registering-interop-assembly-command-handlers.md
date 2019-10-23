---
title: Регистрация обработчиков команд сборки взаимодействия | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbc0d162a11df034bec4d1f357ef8abd106da401
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724692"
---
# <a name="registering-interop-assembly-command-handlers"></a>Регистрация обработчиков команд сборки взаимодействия
Пакет VSPackage должен быть зарегистрирован в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], чтобы интегрированная среда разработки (IDE) правильно маршрутизирует свои команды.

 Реестр можно обновить либо вручную, либо с помощью файла регистратора (RGS). Для получения дополнительной информации см. [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Платформа управляемого пакета (MPF) предоставляет эту функцию через класс <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>.

- [Справочные ресурсы по формату командной таблицы](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) находятся в неуправляемых библиотеках DLL ВСПОМОГАТЕЛЬных интерфейсов.

## <a name="command-handler-registration-of-a-vspackage"></a>Регистрация пакета VSPackage в обработчике команд
 Пакет VSPackage, выступающий в качестве обработчика для команд на основе ПОЛЬЗОВАТЕЛЬСКОГО интерфейса, требует наличия записи реестра с именем после `GUID` VSPackage. Эта запись реестра указывает расположение файла ресурсов пользовательского интерфейса VSPackage и ресурс меню в этом файле. Сама запись реестра находится в папке HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ *\<Version >* \менус, где *\<Version >* — это версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], например 9,0.

> [!NOTE]
> Корневой путь к HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\ *\<Version >* можно переопределить с помощью альтернативного корня при инициализации оболочки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения о корневом пути см. в разделе [Установка пакетов VSPackage с помощью установщик Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Запись реестра ресурсов CTMENU
 Структура записи реестра:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> — это `GUID` VSPackage в форме {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.

 *\<Resource информация >* состоит из трех элементов, разделенных запятыми. Эти элементы по порядку:

 \<*путь к > DLL-файлу ресурсов*, \< >*идентификатор ресурса меню*, \<*версия меню*

 В следующей таблице описаны поля \<*сведений о ресурсах*>.

| Элемент | Описание |
|---------------------------| - |
| \<*путь к DLL-библиотеке ресурсов* > | Это полный путь к библиотеке DLL ресурсов, содержащей ресурс меню, или оставить это поле пустым, указывая на необходимость использования библиотеки DLL ресурсов VSPackage (как указано в подразделе Packages, где зарегистрирован пакет VSPackage).<br /><br /> Это поле остается незаполненным. |
| *идентификатор ресурса меню* \< > | Это идентификатор ресурса `CTMENU` ресурса, который содержит все элементы пользовательского интерфейса для пакета VSPackage, скомпилированные из [vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) -файла. |
| >*версии меню* \< | Это число, используемое в качестве версии ресурса `CTMENU`. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует это значение, чтобы определить необходимость повторного слияния содержимого `CTMENU` ресурса с кэшем всех `CTMENU` ресурсов. Повторная слияние запускается при помощи команды установки devenv.<br /><br /> Изначально это значение должно быть равно 1 и увеличиваться после каждого изменения в `CTMENU`ном ресурсе и перед повторным слиянием. |

### <a name="example"></a>Пример
 Ниже приведен пример нескольких записей ресурсов:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>См. также
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Команды и меню, которые используют сборки взаимодействия](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)