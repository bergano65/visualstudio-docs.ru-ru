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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a5d4daad66ed6a4428724b20093473ba7b93856
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226224"
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

 [out] Возвращает имя потока.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Полученный именем всегда является имя, которое может отображаться, и это имя Описание потока. Имя потока может быть производным от архитектуры среды выполнения, что поддерживает именованные потоки, или его имя на основе обработчика отладки. Кроме того, можно задать имя потока, с помощью вызова [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) метод.

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)