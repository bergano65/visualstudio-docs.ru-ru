---
title: IDebugThread2::SetNextStatement Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b390e5c021fa069ae3fb09eef1978caaf9cc8ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718648"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Устанавливает текущий указатель инструкции к заданному контексту кода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int SetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>Параметры
`pStackFrame`\
Зарезервировано для использования в будущем; установлен на нулевую стоимость.

`pCodeContext`\
(в) Объект [IDebugCodeContext2,](../../../extensibility/debugger/reference/idebugcodecontext2.md) описывающий местоположение кода, которое должно быть выполнено, и его контекст.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. В следующей таблице показаны другие возможные значения.

|Значение|Описание|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|Следующее утверждение не может быть в кадре стека глубже в стеке кадра.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|Следующее утверждение не связано с какой-либо кадром в стеке.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Некоторые отладки двигателей не могут установить следующее заявление после исключения.|

## <a name="remarks"></a>Примечания
 Указатель инструкции указывает следующую инструкцию или инструкцию для выполнения. Этот метод используется для повторной попытки строки исходного кода или для принудительного выполнения для продолжения в другой функции, например.

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
