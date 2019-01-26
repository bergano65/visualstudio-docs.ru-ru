---
title: Флаги возможностей | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cfbc456ea42342187b5d1d3039c10b3336714133
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934196"
---
# <a name="capability-flags"></a>Флаги возможностей
SCC_CAP_*xxx* флаги имеют битовых флагов, используемый для указания возможности подключаемого модуля системы управления версиями. SCC_EXCAP_*xxx* флаги имеют добавочные флаги, которые указывают расширенные возможности и устранить до целых чисел.  
  
|Возможность кода|Значение|Описание:|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_REMOVE`|0x00000001L|Поддерживает [SccRemove](../extensibility/sccremove-function.md) и команду.|  
|`SCC_CAP_RENAME`|0x00000002L|Поддерживает [SccRename](../extensibility/sccrename-function.md) и команду.|  
|`SCC_CAP_DIFF`|0x00000004L|Поддерживает [SccDiff](../extensibility/sccdiff-function.md) и команду.|  
|`SCC_CAP_HISTORY`|0x00000008L|Поддерживает [SccHistory](../extensibility/scchistory-function.md) и команду.|  
|`SCC_CAP_PROPERTIES`|0x00000010L|Поддерживает [SccProperties](../extensibility/sccproperties-function.md) и команду.|  
|`SCC_CAP_RUNSCC`|0x00000020L|Поддерживает [SccRunScc](../extensibility/sccrunscc-function.md) и команду.|  
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Поддерживает [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) и команду.|  
|`SCC_CAP_QUERYINFO`|0x00000080L|Поддерживает [SccQueryInfo](../extensibility/sccqueryinfo-function.md) и команду.|  
|`SCC_CAP_GETEVENTS`|0x00000100L|Поддерживает [SccGetEvents](../extensibility/sccgetevents-function.md) и команду.|  
|`SCC_CAP_GETPROJPATH`|0x00000200L|Поддерживает [SccGetProjPath](../extensibility/sccgetprojpath-function.md) и команду.|  
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Поддерживает [SccAddFromScc](../extensibility/sccaddfromscc-function.md) и команду.|  
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Поддерживает комментарий при извлечении.|  
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Поддерживает комментарий для возврата.|  
|`SCC_CAP_COMMENTADD`|0x00002000L|Поддерживает добавить комментарий.|  
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Поддерживает комментарий на удаление.|  
|`SCC_CAP_TEXTOUT`|0x00008000L|Записывает текст функцию вывода, предоставляемый для интегрированной среды разработки.|  
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Поддерживает хранение файлов без «дельты».|  
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Поддерживает несколько истории файлов.|  
|`SCC_CAP_IGNORECASE`|0x00800000L|Поддерживает сравнение файлов без учета регистра.|  
|`SCC_CAP_IGNORESPACE`|0x01000000L|Поддерживает файлов сравнение, которое не обрабатывает пробел.|  
|`SCC_CAP_POPULATELIST`|0x02000000L|Поддержка поиска лишние файлы.|  
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Поддерживает комментарии для создания проекта.|  
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Поддерживает diff во всех состояниях, если в системе управления.|  
|`SCC_CAP_GET_NOUI`|0x20000000L|Подключаемый модуль не поддерживает пользовательский Интерфейс для Get, но интегрированной среды разработки может по-прежнему вызывать [SccGet](../extensibility/sccget-function.md).|  
|`SCC_CAP_REENTRANT`|0x40000000L|Подключаемый модуль повторными входящими вызовами и потокобезопасным. В версии 1.0 подключаемые модули не предположительно должны были быть реентерабельным и потокобезопасным. Если 1.1 подключаемый модуль устанавливает этот бит, узел может открыть несколько проектов в параллельном режиме.|  
  
## <a name="capability-bits-added-in-version-12"></a>Биты возможностей, добавленных в версии 1.2  
  
|Возможность кода|Значение|Описание:|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Поддерживает [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|  
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Поддерживает [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|  
|`SCC_CAP_BATCH`|0x00040000L|Поддерживает [SccBeginBatch](../extensibility/sccbeginbatch-function.md) и [SccEndBatch](../extensibility/sccendbatch-function.md).|  
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Поддерживает [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|  
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Поддерживает [SccDirDiff](../extensibility/sccdirdiff-function.md).|  
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Поддерживает несколько одновременных извлечений с файлом и [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|  
|`SCC_CAP_SCCFILE`|0x80000000L|Поддерживает *MSSCCPRJ.SCC* файла (при условии переопределение пользователя или администратора) и [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|  
  
## <a name="capability-bits-added-in-version-13"></a>Биты возможностей, добавленных в версии 1.3  
 Эти флаги передаются поочередно для [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) функцию, чтобы определить, поддерживается ли функция.  
  
|Расширенные возможности кода|Значение|Описание|  
|------------------------------|-----------|-----------------|  
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Поддерживает `SCC_CHECKOUT_LOCALVER` вариант для извлечения.|  
|`SCC_EXCAP_BACKGROUND_GET`|2|Поддерживает [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|  
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Поддерживает [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|  
|`SCC_EXCAP_POPULATELIST_DIR`|4|Поддержка поиска Дополнительные каталоги.|  
|`SCC_EXCAP_QUERYCHANGES`|5|Поддерживает перечисление изменений файла.|  
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Поддерживает [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|  
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Поддерживает [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|  
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Поддерживает вызов SccQueryInfo в нескольких потоках.|  
|`SCC_EXCAP_REMOVE_DIR`|9|Поддерживает функцию SccRemoveDir.|  
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Можно удалить извлеченные файлы.|  
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Можно переименовать извлеченных файлов.|  
  
## <a name="see-also"></a>См. также  
 [Подключаемых модулей системы управления версиями](../extensibility/source-control-plug-ins.md)