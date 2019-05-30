---
title: IDebugProgram2::CauseBreak | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a01b5982b4f747bd70c3a35bc0b7191bb54cd21b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311348"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Запрашивает, чтобы программа остановил выполнение следующего время один из потоков попыток запуска.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) событий отправляется в том случае, когда программа попытается Далее для выполнения кода после вызова этого метода.

 Этот метод является асинхронным, в том, что метод немедленно возвращается, не обязательно ожидании остановку программы.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)