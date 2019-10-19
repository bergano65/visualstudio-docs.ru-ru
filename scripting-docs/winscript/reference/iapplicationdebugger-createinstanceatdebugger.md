---
title: 'Иаппликатиондебугжер:: Креатеинстанцеатдебугжер | Документация Майкрософт'
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
ms.openlocfilehash: c15dc5d9b36a718ed41813bac46bc4b9415eb853
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577892"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Позволяет создавать объекты в процессе отладчика по коду, который находится вне процесса отладчика.  
  
> [!IMPORTANT]
> Этот метод не следует реализовывать, так как он позволяет недоверенному коду создавать произвольные объекты в доверенном потоке отладчика.  
  
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
 окне Идентификатор класса (CLSID) создаваемого объекта.  
  
 `pUnkOuter`  
 окне Если `NULL`, объект не создается как часть статистического выражения. В противном случае `pUnkOuter` является указателем на интерфейс `IUnknown` статистического объекта (управляющий `IUnknown`).  
  
 `dwClsContext`  
 окне Контекст для запуска исполняемого кода. Значения берутся из `CLSCTX` перечисления.  
  
 `riid`  
 окне Идентификатор интерфейса, используемый для связи с объектом.  
  
 `ppvObject`  
 заполняет Адрес переменной указателя, получающей указатель интерфейса, запрошенный в `riid`. После успешного возврата * `ppvObject` содержит указатель на запрошенный интерфейс. При сбое \* `ppvObject` содержит `NULL`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод делегирует `CoCreateInstance`.  
  
 Метод в настоящее время не реализован.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)