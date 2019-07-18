---
title: IApplicationDebugger::CreateInstanceAtDebugger | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.CreateInstanceAtDebugger
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95489464128e706e755432bee991c5481f5af8bc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425826"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Позволяет создавать объекты в процессе отладчика, кодом то есть вне процесса в отладчике.  
  
> [!IMPORTANT]
> Этот метод не следует реализовывать, так как она допускает ненадежного кода для создания произвольных объектов в поток доверенных отладчика.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
  
 Метод еще не реализован.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)