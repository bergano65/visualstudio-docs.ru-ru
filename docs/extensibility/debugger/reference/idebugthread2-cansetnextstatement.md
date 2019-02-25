---
title: IDebugThread2::CanSetNextStatement | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43ec2c5d157832834f76834f7b93e193629b66d8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703049"
---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
Определяет, можно ли установить текущего указателя инструкций в указанном кадре стека.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CanSetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int CanSetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

#### <a name="parameters"></a>Параметры
 `pStackFrame` Зарезервировано для будущего использования; присвоено значение null. Если это значение null, используется текущий кадр стека.

 `pCodeContext`

 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , описывающий расположение кода должна быть выполнена и его контекста.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Если этот метод возвращает `S_OK`, затем вызвать [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md) метод фактически задать следующий оператор.

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)