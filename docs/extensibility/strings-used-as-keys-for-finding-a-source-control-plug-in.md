---
title: Строки, используемые в качестве ключей поиска подключаемого модуля системы управления версиями | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31c2b30fb41976cdbbab13fa22d438c63bddbbef
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331707"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Строки, используемые в качестве ключей поиска подключаемого модуля системы управления версиями
Следующие строки ключи для доступа к реестру для поиска сведений о системы управления версиями подключаемого модуля.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH`, и `STR_SCCPROVIDERNAME` разделов реестра или значения, используемые для регистрации библиотек DLL в качестве подключаемого модуля системы управления версиями для Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE`, и `SCC_STATUS_FILE` используются для описания формата MSSCCPRJ. Файл SCC.

## <a name="string-keys-and-values"></a>Строковых ключей и значений

|Ключ|Значение|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|Системы управления исходным кодом|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ. SCC|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Файл исходного кода элемента управления|
|`SCC_NSE`|Расширение пространства имен|
|`SCC_NSE_PREFIX`|Префикс протокола|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>См. также
- [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)
- [Практическое руководство. Установка подключаемого модуля системы управления версиями](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Файл MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)