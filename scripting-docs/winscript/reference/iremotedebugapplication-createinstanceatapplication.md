---
title: IRemoteDebugApplication::CreateInstanceAtApplication | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.CreateInstanceAtApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CreateInstanceAtApplication
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e17c5abcb21bfaad6de948c3676d29232da66cf
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146296"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Позволяет создавать объекты в процессе приложения кодом то есть вне процесса для приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
 [in] Если `NULL`, объект не была создана как часть агрегата. В противном случае `pUnkOuter` — это указатель на Агрегатный объект `IUnknown` интерфейс (управляющий `IUnknown`).  
  
 `dwClsContext`  
 [in] Контекст для выполняющегося исполняемого кода. Значения берутся из перечисления `CLSCTX`.  
  
 `riid`  
 [in] Идентификатор интерфейса, используемый для взаимодействия с объектом.  
  
 `ppvObject`  
 [out] Адрес переменной указателя, получающей указатель интерфейса, запрашиваемый в `riid`. При успешном возвращении *`ppvObject` содержит запрошенный указатель интерфейса. В случае сбоя \* `ppvObject` содержит `NULL`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод делегирует `CoCreateInstance`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)