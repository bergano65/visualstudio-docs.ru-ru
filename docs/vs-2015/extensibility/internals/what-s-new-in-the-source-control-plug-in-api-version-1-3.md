---
title: Что&#39;API версии 1.3 подключаемого модуля управления возможности в источнике | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d5333a5b44e9c990843e66da357578e4a90d210
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992429"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Что&#39;возможности в источнике управления API версии 1.3 подключаемого модуля
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

API подключаемых модулей управления исходной версии 1.3 вводит следующие новые функции для предоставления более расширенные функции управления.  
  
## <a name="changes"></a>Изменения  
 Следующие функции, добавленные в API подключаемых модулей управления исходной версии 1.3.  
  
|Функция|Обзор|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Позволяет биты дополнительных возможностей требуется получить сведения об|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Анализ файлов, которые имеют более новые версии в базу данных контроля версий чем на локальном диске|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Позволяет осмысленно изучать состояния изменения имен (переименование, добавления и удаления) для указанных файлов|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Анализ файлов и каталогов в базе данных системы управления версиями|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Добавляет указанный список файлов из базы данных системы управления версиями в текущий проект|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Выполняет автоматическую «получить» заданного файла (пользовательский интерфейс не отображается)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Разрешает доступ к определяемым пользователем параметрам|  
  
## <a name="see-also"></a>См. также  
 [Начало работы](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
