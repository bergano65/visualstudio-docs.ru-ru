---
title: "Интерфейс IDebugExpressionContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionContext Interface
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpressionContext — интерфейс"
ms.assetid: 52af82e8-0dec-49e2-a7f3-d00f66ca1401
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugExpressionContext
Представляет контекст, в котором выражения можно вычислить.  Объект кадра стека реализует этот интерфейс.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDebugExpressionContext` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)|Создает выражение отладки для указанного текста.|  
|[IDebugExpressionContext::GetLanguageInfo](../../winscript/reference/idebugexpressioncontext-getlanguageinfo.md)|Возвращает имя и идентификатор GUID для языка, которому принадлежит данный контекст.|