---
title: IActiveScriptSiteDebug32::GetDocumentContextFromPosition | Документация Майкрософт
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
ms.openlocfilehash: 9a52abcfa4defb49526f944469c95a2247f5d85c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992511"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
Используемый модуль языка делегировать `IDebugCodeContext::GetSourceContext`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
 [in] Символ, смещение относительно начала блока скрипта или скриптлета.  
  
 `uNumChars`  
 [in] Число символов в данном контексте.  
  
 `ppsc`  
 [out] Контекст документа, соответствующий диапазону этого позицию символа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Модулям языка этот метод позволяет делегировать `IDebugCodeContext::GetSourceContext`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)