---
title: Строки, используемые в качестве ключей для поиска подключаемого подключения к управлению источником (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f9333ff1b6742ca14dc5541bd15e92b2eb39085
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699713"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Строки, используемые в качестве ключей поиска подключаемого модуля системы управления версиями
Следующие строки являются ключами для доступа к реестру, чтобы найти информацию о плагине управления исходным кодом.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` `STR_SCCPROVIDERPATH`, `STR_SCCPROVIDERNAME` и являются ключами реестра или значения, используемые для регистрации DLL в качестве подключаемого источника управления для Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` `SCC_KEY, SCC_FILE_SIGNATURE`, `SCC_STATUS_FILE` , и используются для описания формата MSSCCPRJ. Файл SCC.

## <a name="string-keys-and-values"></a>Строки ключи и ценности

|Клавиши|Значение|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Программное обеспечение-ИсточникКодКонтрольПровайдер|
|`STR_PROVIDERREGKEY`|ПоставщикRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|Управление исходным кодом|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ. Scc|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Файл управления исходным кодом|
|`SCC_NSE`|Расширение пространства имен|
|`SCC_NSE_PREFIX`|Протокальная префикс|
|`SCC_NSE_DisableOpenSCC`|ОтключитьOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|СправкаСбор|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Программное обеспечение(Microsoft-SourceSafe|

## <a name="see-also"></a>См. также
- [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)
- [Практическое руководство. Установка подключаемого модуля системы управления версиями](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Файл MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
