---
title: "IRemoteDebugApplication::CreateInstanceAtApplication | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IRemoteDebugApplication.CreateInstanceAtApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CreateInstanceAtApplication
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2185987f6b635dae4d537231fca3327d0aed003
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Позволяет создавать объекты в процессе приложения с кодом, вне процесса для приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CreateInstanceAtApplication(  
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
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)