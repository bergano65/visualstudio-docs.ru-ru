---
title: ICanHandleException::CanHandleException | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ICanHandleException.CanHandleException
apilocation:
- scrobj.dll
helpviewer_keywords:
- ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 784463f9e465aac005f5454be28a0043069dcb69
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090003"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Определяет, если вызывающий объект обработчика сценариев может обрабатывать указанное исключение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pExcepInfo`  
 [in] Указатель на `EXCEPINFO` структуру, содержащую сведения, который выводится при обнаружении обработчика исключений нет.  
  
 `pvar`  
 [in] Значение, связанное с исключением, например, значение, вызванное `throw` инструкции. Этот параметр может иметь значение `NULL`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Вызывающий объект может обработать исключение|  
|`E_FAIL`|Вызывающий объект не может обработать исключение.|  
  
## <a name="remarks"></a>Примечания  
 Если в вызове `IDispatchEx::InvokeEx`, или аналогичного метода, возникает исключение, обработчик проверки скрипта в вызывающем коде в цепочке вызывающий объект скрипта, который поддерживает `ICanHandleException` интерфейс, а также указывает, что он может обработать исключение. Если вызывающий объект может обработать исключение, обработчик сценария останавливается.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ICanHandleException](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)