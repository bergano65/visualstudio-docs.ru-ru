---
title: 'Идебугдокументконтекст:: Енумкодеконтекстс | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentContext.EnumCodeContexts
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentContext::EnumCodeContexts
ms.assetid: fb0aa64e-c458-4ef1-bcd8-5cebdc972549
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 790fd55493bfb24b32400bc73ae8a1799a279625
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573483"
---
# <a name="idebugdocumentcontextenumcodecontexts"></a>IDebugDocumentContext::EnumCodeContexts
Перечисление контекстов кода, связанных с этим контекстом документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT EnumCodeContexts(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppescc`  
 заполняет Контексты кода, связанные с этим текстом документа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Документ обычно связывается только с одним контекстом кода, если только документ не является включаемым файлом или шаблоном.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md)