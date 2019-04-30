---
title: IDebugThread2::GetName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04a76c88e5fd3eee146f6c174087298bac2b6974
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915631"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Возвращает имя потока.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

#### <a name="parameters"></a>Параметры
 `pbstrName`

 [out] Возвращает имя потока.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Полученный именем всегда является имя, которое может отображаться, и это имя Описание потока. Имя потока может быть производным от архитектуры среды выполнения, что поддерживает именованные потоки, или его имя на основе обработчика отладки. Кроме того, можно задать имя потока, с помощью вызова [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) метод.

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)