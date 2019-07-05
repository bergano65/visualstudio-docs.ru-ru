---
title: IActiveScriptSiteDebug::GetDocumentContextFromPosition | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetDocumentContextFromPosition
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df6c59fea5cfd60b6ae9a1b34e7000bd38dd9920
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992552"
---
# <a name="iactivescriptsitedebuggetdocumentcontextfromposition"></a>IActiveScriptSiteDebug::GetDocumentContextFromPosition
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
 [Интерфейс IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)