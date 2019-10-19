---
title: 'IRemoteDebugApplication:: Креатеинстанцеатаппликатион | Документация Майкрософт'
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
ms.openlocfilehash: 285e5df6960e3188ffe1ce17b1fc4f43626a3d74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572308"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Позволяет создавать объекты в процессе приложения по коду, который находится вне процесса приложения.  
  
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
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)