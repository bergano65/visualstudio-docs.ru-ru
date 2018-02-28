---
title: "IDebugApplication::AddStackFrameSniffer | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplication.AddStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::AddStackFrameSniffer
ms.assetid: a7a9684a-14c5-415a-ae63-a17397d58d07
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89faa6481bd5e5934ae2d3b85a0bade83949633a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationaddstackframesniffer"></a>IDebugApplication::AddStackFrameSniffer
Добавляет поставщик перечислитель кадр стека для этого приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT AddStackFrameSniffer(  
   IDebugStackFrameSniffer*  pdsfs,  
   DWORD*                    pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdsfs`  
 [in] Поставщик перечислитель кадра стека для добавления к этому приложению.  
  
 `pdwCookie`  
 [out] Файл cookie, который используется для удаления этого поставщика перечислитель кадра стека из приложения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Несмотря на то, что модули языка обычно вызывает этот метод для предоставления их кадры стека в отладчик, возможно, других лиц для предоставления кадры стека.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)   
 [Интерфейс IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)