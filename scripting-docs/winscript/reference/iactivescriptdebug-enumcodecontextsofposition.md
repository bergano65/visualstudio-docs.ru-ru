---
title: 'Иактивескриптдебуг:: Енумкодеконтекстсофпоситион | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::EnumCodeContextsOfPosition
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aedfe5d40d8f4086e30f3a62c070b8ccd5ef2388
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572779"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Используется интеллектуальным узлом для делегирования метода `IDebugDocumentContext::EnumCodeContexts`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwSourceContext`  
 окне Контекст источника, предоставленный для `IActiveScriptParse::ParseScriptText` или `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 окне Смещение символов относительно начала текста скрипта.  
  
 `uNumChars`  
 окне Число символов в этом контексте.  
  
 `ppescc`  
 заполняет Перечислитель контекстов кода в указанном диапазоне.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Интеллектуальные узлы используют этот метод для делегирования метода `IDebugDocumentContext::EnumCodeContexts`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса иактивескриптдебуг](../../winscript/reference/iactivescriptdebug-interface.md)  
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)