---
title: "IApplicationDebugger::CreateInstanceAtDebugger | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IApplicationDebugger.CreateInstanceAtDebugger
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6495c2d8782d1128700bdfb6d4081b80ffae878
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Позволяет создавать объекты в процессе отладчика с кодом, out-of-process в отладчик.  
  
> [!IMPORTANT]
>  Этот метод не должен быть реализован, так как она допускает ненадежного кода для создания произвольных объектов в поток доверенных отладчика.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CreateInstanceAtDebugger(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `rclsid`  
 [in] Идентификатор (класса CLSID) создаваемого объекта класса.  
  
 `pUnkOuter`  
 [in] Если `NULL`, объект не создается в ходе статистической обработки. В противном случае `pUnkOuter` — это указатель на Агрегатный объект `IUnknown` интерфейса (Управление `IUnknown`).  
  
 `dwClsContext`  
 [in] Контекст для выполняющегося исполняемого кода. Значения берутся из перечисления `CLSCTX`.  
  
 `riid`  
 [in] Идентификатор интерфейса, используемый для связи с объектом.  
  
 `ppvObject`  
 [out] Адрес переменной указателя, получающей указатель интерфейса, запрашиваемый в `riid`. После успешного возврата *`ppvObject` содержит указатель на запрошенный интерфейс. После сбоя \* `ppvObject` содержит `NULL`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод делегирует `CoCreateInstance`.  
  
 Метод не реализован в настоящее время.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)