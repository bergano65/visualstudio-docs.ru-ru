---
title: IDebugProgram3::ExecuteOnThread | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 798a0caca394a21d6ee12a99efeacb2f27f6969c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343605"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Выполняет программу отладчика. Поток возвращается для предоставления информации отладчика, в каком потоке пользователь просматривает при выполнении программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Параметры
`pThread`\
[in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) объекта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Существует три разных способа, что отладчик можно возобновить выполнение после остановки:

- Выполните: Отмена любой предыдущем шаге и выполняется до следующей точки останова, и т. д.

- Шаг. Отменить какой-либо шаг старый и запустить до завершения нового шага.

- По-прежнему: Снова запустите и оставить все старые шаг active.

  Поток, передаваемый `ExecuteOnThread` полезна при принятии решения о этап для отмены. Если вы не знаете потоке, выполнение отменяет все шаги. С помощью базы знаний потока достаточно для отмены шага в активном потоке.

## <a name="see-also"></a>См. также
- [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)