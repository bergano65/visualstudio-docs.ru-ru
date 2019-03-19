---
title: IDebugCodeContext::GetDocumentContext | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCodeContext.GetDocumentContext
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugCodeContext::GetDocumentContext
ms.assetid: 9fe17b65-3a8c-4d21-9b66-0e4ff303af72
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48c707432ddb94fae111c971b89c8ff74f34ac21
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150781"
---
# <a name="idebugcodecontextgetdocumentcontext"></a>IDebugCodeContext::GetDocumentContext
Возвращает контекст документа, связанный с данным контекстом кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppsc`  
 [out] Контекст документа, связанный с данным контекстом кода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Для текстовых документов позиция символа диапазона должен быть текст для всей инструкции. Это позволяет отладчику интегрированной среды разработки, чтобы выделить текущий оператор источника.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugCodeContext](../../winscript/reference/idebugcodecontext-interface.md)