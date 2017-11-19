---
title: "Строки, которые используются в качестве ключа для поиска подключаемый модуль системы управления версиями | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d2ee5e741466b7976c8b397928cd9fccd12472fe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Строки, которые используются в качестве ключа для поиска подключаемый модуль системы управления версиями
Следующие строки являются ключевыми для доступа к реестру для поиска сведений о системы управления версиями подключаемого модуля.  
  
 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH`, и `STR_SCCPROVIDERNAME` разделы реестра и значения, используемые для регистрации библиотеки DLL в качестве подключаемого модуля системы управления версиями для Visual Studio.  
  
 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE`, и `SCC_STATUS_FILE` используются для описания формата MSSCCPRJ. Файл SCC.  
  
## <a name="string-keys-and-values"></a>Строковых ключей и значений  
  
|Ключ|Значение|  
|---------|-----------|  
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|  
|`STR_PROVIDERREGKEY`|ProviderRegKey|  
|`STR_SCCPROVIDERPATH`|Данный параметр|  
|`STR_SCCPROVIDERNAME`|SCCServerName|  
|`STR_SCC_INI_SECTION`|Управление исходным кодом|  
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
 [Подключаемые модули управления версиями](../extensibility/source-control-plug-ins.md)   
 [Как: установить подключаемый модуль системы управления версиями](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Файл MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)