---
title: ICanHandleException::CanHandleException | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 406787d5ee6811b80f9e6831e5a67cab8367e7d0
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146491"
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