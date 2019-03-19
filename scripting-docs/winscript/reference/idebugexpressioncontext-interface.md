---
title: Интерфейс IDebugExpressionContext | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext Interface
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext interface
ms.assetid: 52af82e8-0dec-49e2-a7f3-d00f66ca1401
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5920d644922b15f193ee396ea0c6bddb8a574698
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156675"
---
# <a name="idebugexpressioncontext-interface"></a>Интерфейс IDebugExpressionContext
Представляет контекст, где выражения можно вычислить. Объект кадра стека реализует этот интерфейс.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugExpressionContext` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)|Создает выражение отладки для указанного текста.|  
|[IDebugExpressionContext::GetLanguageInfo](../../winscript/reference/idebugexpressioncontext-getlanguageinfo.md)|Возвращает имя и идентификатор GUID для языка, которому принадлежит этот контекст.|