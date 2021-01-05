---
title: Строки, используемые в качестве ключей для поиска подключаемого модуля системы управления версиями
description: Сведения о строках, которые являются ключами для доступа к реестру, чтобы найти сведения о подключаемом модуле системы управления версиями.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: a99d64873018885c35c066f05e6a3a8919868d72
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715318"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Строки, используемые в качестве ключей поиска подключаемого модуля системы управления версиями
Следующие строки являются ключами для доступа к реестру для поиска сведений о подключаемом модуле системы управления версиями.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` , `STR_SCCPROVIDERPATH` и `STR_SCCPROVIDERNAME` — это разделы реестра или значения, используемые для регистрации библиотеки DLL в качестве подключаемого модуля системы управления версиями для Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` , `SCC_KEY, SCC_FILE_SIGNATURE` и `SCC_STATUS_FILE` используются для описания формата мссккпрж. Файл SCC.

## <a name="string-keys-and-values"></a>Строковые ключи и значения

|Ключ|Значение|
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

## <a name="see-also"></a>См. также раздел
- [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)
- [Практическое руководство. Установка подключаемого модуля системы управления версиями](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Файл MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
