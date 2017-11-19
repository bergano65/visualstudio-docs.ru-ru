---
title: "IActiveScriptDebug::EnumCodeContextsOfPosition | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation: jscript.dll
helpviewer_keywords: IActiveScriptDebug::EnumCodeContextsOfPosition
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40fd8e2d19d3949ff26811956ae3d203871e5510
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Используемые промежуточный узел делегировать `IDebugDocumentContext::EnumCodeContexts` метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwSourceContext`  
 [in] Источник контекста, предоставляемая `IActiveScriptParse::ParseScriptText` или `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Знак смещения относительно начала текста сценария.  
  
 `uNumChars`  
 [in] Число символов в данном контексте.  
  
 `ppescc`  
 [out] Перечислитель контекстов кода в указанном диапазоне.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Промежуточные узлы используйте этот метод, чтобы делегировать `IDebugDocumentContext::EnumCodeContexts` метод.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)