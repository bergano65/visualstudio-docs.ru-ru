---
title: IDebugProgram2::CauseBreak | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06b392dd10c364e746f592a4d0ffd9ac32ca7df9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720215"
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