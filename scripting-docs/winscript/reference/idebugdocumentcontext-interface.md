---
title: "Интерфейс IDebugDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentContext — интерфейс"
ms.assetid: 665ee08a-5c6a-4ab1-ab93-de376acc9a74
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Интерфейс IDebugDocumentContext
Предоставляет абстрактное представление частью отлаживаемого документа.  Для текстовых документов, это представление состоит из диапазона позиции символа.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDebugDocumentContext` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugDocumentContext::GetDocument](../../winscript/reference/idebugdocumentcontext-getdocument.md)|Возвращает документ, который содержит данный контекст.|  
|[IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)|Перечисляет контексты кода, связанные с данным контекстом документа.|