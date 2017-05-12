---
title: "Интерфейс IDebugDocumentTextExternalAuthor | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentTextExternalAuthor — интерфейс"
ms.assetid: 0b04de1b-f922-4526-af4e-c0af2b7c1ce4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugDocumentTextExternalAuthor
Позволяет безопасно на внешние редакторы правка на основе файла документы отладчика, уведомляя документ, когда исходный файл изменить.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDebugDocumentTextExternalAuthor` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugDocumentTextExternalAuthor::GetPathName](../../winscript/reference/idebugdocumenttextexternalauthor-getpathname.md)|Возвращает полный путь и имя файла документа.|  
|[IDebugDocumentTextExternalAuthor::GetFileName](../../winscript/reference/idebugdocumenttextexternalauthor-getfilename.md)|Возвращает имя документа без информации пути.|  
|[IDebugDocumentTextExternalAuthor::NotifyChanged](../../winscript/reference/idebugdocumenttextexternalauthor-notifychanged.md)|Уведомляет основное приложение о том, что источник документа был изменен.|