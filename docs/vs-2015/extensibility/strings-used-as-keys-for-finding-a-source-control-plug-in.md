---
title: Строки, используемые в качестве ключей для поиска подключаемого модуля системы управления версиями | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 83ba843e318aac6a74d318978e42e2f81802d8ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160576"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Строки, используемые в качестве ключей поиска подключаемого модуля системы управления версиями
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Следующие строки являются ключами для доступа к реестру для поиска сведений о подключаемом модуле системы управления версиями.  
  
 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` , `STR_SCCPROVIDERPATH` и `STR_SCCPROVIDERNAME` — это разделы реестра или значения, используемые для регистрации библиотеки DLL в качестве подключаемого модуля системы управления версиями для Visual Studio.  
  
 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` , `SCC_KEY, SCC_FILE_SIGNATURE` и `SCC_STATUS_FILE` используются для описания формата мссккпрж. Файл SCC.  
  
## <a name="string-keys-and-values"></a>Строковые ключи и значения  
  
|Клавиши|Значение|  
|---------|-----------|  
|`STR_SCC_PROVIDER_REG_LOCATION`|софтваре\саурцекодеконтролпровидер|  
|`STR_PROVIDERREGKEY`|провидеррегкэй|  
|`STR_SCCPROVIDERPATH`|скксерверпас|  
|`STR_SCCPROVIDERNAME`|скксервернаме|  
|`STR_SCC_INI_SECTION`|Управление исходным кодом|  
|`STR_SCC_INI_KEY`|саурцекодеконтролпровидер|  
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|  
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|  
|`SCC_STATUS_FILE`|МССККПРЖ. СРЕДСТВО|  
|`SCC_KEY`|SCC|  
|`SCC_FILE_SIGNATURE`|Файл управления исходным кодом|  
|`SCC_NSE`|Расширение пространства имен|  
|`SCC_NSE_PREFIX`|Префикс протокола|  
|`SCC_NSE_DisableOpenSCC`|дисаблеопенфромсаурцеконтрол|  
|`STR_SCCHELPCOLLECTION`|хелпколлектион|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|софтваре\микрософт\саурцесафе|  
  
## <a name="see-also"></a>См. также:  
 [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)   
 [Как установить подключаемый модуль системы управления версиями](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Файл MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
