---
title: "IDebugCodeContext::GetDocumentContext | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugCodeContext.GetDocumentContext
apilocation: jscript.dll
helpviewer_keywords: IDebugCodeContext::GetDocumentContext
ms.assetid: 9fe17b65-3a8c-4d21-9b66-0e4ff303af72
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 098d57a5ff0ba14b1dd493ad772eee595a10ec9a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugcodecontextgetdocumentcontext"></a>IDebugCodeContext::GetDocumentContext
Возвращает контекст документ, связанный с данным контекстом кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppsc`  
 [out] Контекст документ, связанный с данным контекстом кода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Для текстовых документов позиции символа диапазона должен быть текст для всего отчета. Это позволяет отладчику интегрированной среды разработки, чтобы выделить текущую инструкцию источника.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugCodeContext](../../winscript/reference/idebugcodecontext-interface.md)