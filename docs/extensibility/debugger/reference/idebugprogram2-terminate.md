---
title: IDebugProgram2::Terminate | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16a6d60173090642bda7d8fd940ecf0699e1d7ec
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331501"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Завершает программу.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Если это возможно программа будет завершен и выгружать из процесса; в противном случае модуль отладки (DE) выполнит необходимые операции очистки.

 Этот метод или [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) метод вызывается средой IDE, обычно в ответ на пользователя к остановке всех отладки. Реализация этого метода в идеале, завершение работы программы в рамках процесса. Если это невозможно, DE следует привести программы к работе в этом процессе большее количество (и выполнить необходимую очистку). Если `IDebugProcess2::Terminate` метод был вызван в интегрированной среде разработки, весь процесс завершается через некоторое время после `IDebugProgram2::Terminate` вызывается метод.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)