---
title: "ICanHandleException::CanHandleException | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ICanHandleException.CanHandleException
apilocation: scrobj.dll
helpviewer_keywords: ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15612330f160f694202bb2158f970e0633fe53bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Определяет, если вызывающий объект обработчика сценариев может обработать указанное исключение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pExcepInfo`  
 [in] Указатель на `EXCEPINFO` структуру, содержащую сведения, которые должны отображаться, если не обнаруживается.  
  
 `pvar`  
 [in] Значение, связанное с исключением, например выводится значение `throw` инструкции. Этот параметр может иметь значение `NULL`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Вызывающий объект может обработать исключение|  
|`E_FAIL`|Вызывающий объект не может обработать исключение.|  
  
## <a name="remarks"></a>Примечания  
 Если вызов `IDispatchEx::InvokeEx`, или аналогичным методом, приводит к возникновению исключения, проверки обработчик скриптов для вызывающему объекту в цепочке вызывающий скрипт, поддерживающий `ICanHandleException` интерфейс и указывает, что он может обработать исключение. Если вызывающий объект может обработать исключение, останавливает обработчик сценариев.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ICanHandleException](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)