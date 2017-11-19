---
title: "Какой &#39; s введено в источнике управления подключаемого модуля API версии 1.3 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd0c23258034fb99f5e2e4e0c86ca9e61c3d68ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Какой &#39; новые возможности подключаемого модуля API версиями 1.3
API подключаемых модулей управления исходной версии 1.3 появились следующие новые функции для предоставления более сложных элементов управления.  
  
## <a name="changes"></a>Изменения  
 Следующие функции являются новыми для API подключаемых модулей управления исходной версии 1.3:  
  
|Функция|Обзор|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Обеспечивает дополнительные возможности битов в отчетах|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Анализ файлов, имеющих более новых версий базы данных версии элемента управления на локальном диске|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Позволяет проверять состояние имя изменения (операции переименования, добавления и удаления) для указанных файлов|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Анализ файлов и каталогов в базе данных управления версиями|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Добавляет указанный список файлов из базы данных управления версии в текущий проект|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Выполняет автоматическую «получить» заданного файла (пользовательский интерфейс не отображается)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Разрешает доступ к параметрам конкретного пользователя|  
  
## <a name="see-also"></a>См. также  
 [Начало работы](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)