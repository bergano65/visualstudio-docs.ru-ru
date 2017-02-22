---
title: "Новые возможности в подключаемый модуль API версия системы управления версиями 1.3 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "системы управления версиями подключаемые модули, новые возможности API v1.3"
  - "что такое новый [Visual Studio SDK] источник подключаемые модули управления"
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Новые возможности в подключаемый модуль API версия системы управления версиями 1.3
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Версия 1,3 API системы управления версиями подключаемых модулей появились следующие новые функции для получения более дополнительных элементов управления.  
  
## Изменения  
 Следующие новые функции в версии 1.3 API системы управления версиями вставляемой:  
  
|Функция|Общие сведения|  
|-------------|--------------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Обеспечивает дополнительные возможности, которые необходимо сообщить биты|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Разрешает вопросы файлов, которые имеют более новые версии в базе данных системы управления версиями, чем на локальном диске|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Разрешает вопросы состояния перемен имени \(переименование добавления и удаления\) для указанных файлов|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Разрешает вопросы каталогов и файлов в базу данных системы управления версиями|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Добавляет указанный список файлов из базы данных системы управления версиями в текущий проект|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Выполняет проверку пользователя "get" указанных файлов \(ни пользовательский интерфейс не показан\)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Разрешает доступ к параметрам пользователя|  
  
## См. также  
 [Начало работы](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Новые возможности в подключаемый модуль API версия системы управления версиями 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)