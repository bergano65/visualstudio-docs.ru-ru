---
title: IDebugThread2::SetThreadName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetThreadName
helpviewer_keywords:
- IDebugThread2::SetThreadName
ms.assetid: fa934121-3f58-44dc-9c30-d3f752e44c8b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aa21a4ff708c8f9cad04e7124f0e4d16378256dd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320029"
---
# <a name="idebugthread2setthreadname"></a>IDebugThread2::SetThreadName
Задает имя потока.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetThreadName ( 
   LPCOLESTR pszName
);
```

```csharp
int SetThreadName ( 
   string pszName
);
```

## <a name="parameters"></a>Параметры
`pszName`\
[in] Имя потока.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Чтобы получить имя потока, вызовите [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md) метод.

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)