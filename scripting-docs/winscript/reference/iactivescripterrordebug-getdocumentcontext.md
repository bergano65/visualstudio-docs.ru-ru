---
title: 'Иактивескриптеррордебуг:: Жетдокументконтекст | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptErrorDebug.GetDocumentContext
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptErrorDebug::GetDocumentContext
ms.assetid: 567601a1-551a-4905-bda1-1f54610174f4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e1a6e2502e9329a7a56a7359e11a934f0ae5985
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576335"
---
# <a name="iactivescripterrordebuggetdocumentcontext"></a>IActiveScriptErrorDebug::GetDocumentContext
Предоставляет контекст документа для этой ошибки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppssc  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppssc`  
 заполняет Контекст документа для этой ошибки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Диапазон символьных позиций контекста документа должен включать все символы, соответствующие данной ошибке.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)