---
title: Флаги возможностей Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9660cbe5a18e82974858fa4d923a38fc73e773f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739867"
---
# <a name="capability-flags"></a>Флаги возможностей
Флаги SCC_CAP_*xxx* — это бибытые флаги, используемые для обозначения возможностей плагина управления исходным управлением. Флаги SCC_EXCAP_*xxx* являются постепенными флагами, указывающими на расширенные возможности и решимость к значениям.

|Код возможностей|Значение|Описание|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|Поддерживает [SccRemove](../extensibility/sccremove-function.md) и команду.|
|`SCC_CAP_RENAME`|0x00000002L|Поддерживает [SccRename](../extensibility/sccrename-function.md) и команду.|
|`SCC_CAP_DIFF`|0x00000004L|Поддерживает [SccDiff](../extensibility/sccdiff-function.md) и команду.|
|`SCC_CAP_HISTORY`|0x00000008L|Поддерживает [SccИстория](../extensibility/scchistory-function.md) и команда.|
|`SCC_CAP_PROPERTIES`|0x00000010L|Поддерживает [SccProperties](../extensibility/sccproperties-function.md) и команду.|
|`SCC_CAP_RUNSCC`|0x0000020L|Поддерживает [SccRunScc](../extensibility/sccrunscc-function.md) и команду.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x0000040L|Поддерживает [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) и команду.|
|`SCC_CAP_QUERYINFO`|0x0000080L|Поддерживает [команду Scc'ryinfo](../extensibility/sccqueryinfo-function.md) и команду.|
|`SCC_CAP_GETEVENTS`|0x0000100L|Поддерживает [SccGetEvents](../extensibility/sccgetevents-function.md) и команду.|
|`SCC_CAP_GETPROJPATH`|0x0000200L|Поддерживает [SccGetProjPath](../extensibility/sccgetprojpath-function.md) и команду.|
|`SCC_CAP_ADDFROMSCC`|0x0000400L|Поддерживает [SccAddFromScc](../extensibility/sccaddfromscc-function.md) и команду.|
|`SCC_CAP_COMMENTCHECKOUT`|0x0000800L|Поддерживает комментарий о выезде.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Поддерживает комментарий о регистрации.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Поддерживает комментарий на Добавить.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Поддерживает комментарий на Удаление.|
|`SCC_CAP_TEXTOUT`|0x00008000L|Записывает текст в функцию вывода, предоставленную IDE.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Поддерживает хранение файлов без дельт.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Поддерживает несколько историй файлов.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Поддерживает сравнение файлов без чувствительного файла.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|Поддерживает сравнение файлов, которое игнорирует белое пространство.|
|`SCC_CAP_POPULATELIST`|0x02000000L|Поддерживает поиск дополнительных файлов.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Поддерживает комментарии по созданию проекта.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Поддерживает дифф во всех штатах, если под контролем.|
|`SCC_CAP_GET_NOUI`|0x20000000L|Подключаемый модуль не поддерживает uI для Get, но IDE все еще может вызвать [SccGet](../extensibility/sccget-function.md).|
|`SCC_CAP_REENTRANT`|0x40000000L|Подключаемый модуль является реативным и безопасным для потоков. В версии 1.0 не предполагалось, что плагины не являются реативным и безопасным для потоков. Если плагин 1.1 устанавливает этот бит, хост может открыть несколько проектов параллельно.|

## <a name="capability-bits-added-in-version-12"></a>Бит возможностей, добавленных в версию 1.2

|Код возможностей|Значение|Описание|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Поддерживает [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Поддерживает [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|
|`SCC_CAP_BATCH`|0x00040000L|Поддерживает [SccBeginBatch](../extensibility/sccbeginbatch-function.md) и [SccEndBatch](../extensibility/sccendbatch-function.md).|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Поддерживает [SccDir-КуирайИнфо](../extensibility/sccdirqueryinfo-function.md).|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Поддерживает [SccDirDiff](../extensibility/sccdirdiff-function.md).|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Поддерживает несколько проверок в файле и [SccIsMultiCheckoutEnabled.](../extensibility/sccismulticheckoutenabled-function.md)|
|`SCC_CAP_SCCFILE`|0x80000000L|Поддерживает файл *MSSCCPRJ.SCC* (при условии переопределения пользователя/администратора) и [SccWillCreateSccFile.](../extensibility/sccwillcreatesccfile-function.md)|

## <a name="capability-bits-added-in-version-13"></a>Бит возможностей, добавленных в версию 1.3
 Эти флаги передаются по одному функции [SccGetExtendedCapabilities,](../extensibility/sccgetextendedcapabilities-function.md) чтобы определить, поддерживается ли возможность.

|Расширенный код возможностей|Значение|Описание|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Поддерживает `SCC_CHECKOUT_LOCALVER` опцию для выезда.|
|`SCC_EXCAP_BACKGROUND_GET`|2|Поддерживает [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Поддерживает [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Поддерживает поиск дополнительных каталогов.|
|`SCC_EXCAP_QUERYCHANGES`|5|Поддерживает перечисление изменений файлов.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Поддерживает [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Поддерживает [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Поддерживает вызов Scc's'ryInfo на нескольких потоках.|
|`SCC_EXCAP_REMOVE_DIR`|9|Поддерживает функцию SccRemoveDir.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Можно удалить проверенные файлы.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Можно переименовать проверенные файлы.|

## <a name="see-also"></a>См. также
- [Плагины управления исходным элементом](../extensibility/source-control-plug-ins.md)
