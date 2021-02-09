---
title: 'IDebugThread2:: Name | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7a8a7a4f041e2a38cf1e24e8cf156d3e595010b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893858"
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

## <a name="parameters"></a>Параметры
`pbstrName`\
заполняет Возвращает имя потока.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Извлеченное имя всегда является именем, которое может быть отображено, и это имя описывает поток. Имя потока может быть производным от архитектуры времени выполнения, которая поддерживает именованные потоки, или именем, полученным от модуля отладки. Кроме того, имя потока можно задать с помощью вызова метода [сетсреаднаме](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
