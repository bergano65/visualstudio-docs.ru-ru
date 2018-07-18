---
title: IActiveScriptSiteDebug32::GetDocumentContextFromPosition | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 71136a1b3cb136cbc0a97cf39f59f1f4e950048b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725084"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
Использовать обработчик языка для делегирования `IDebugCodeContext::GetSourceContext`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwSourceContext`  
 [in] Исходное содержимое, предоставляемое `ParseScriptText` или `AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Знак смещения относительно начала блока сценария или сценариев.  
  
 `uNumChars`  
 [in] Число символов в данном контексте.  
  
 `ppsc`  
 [out] Контекст документа, соответствующий диапазону этой позиции символа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Язык обработчики используют этот метод позволяет делегировать `IDebugCodeContext::GetSourceContext`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)