---
title: IDebugEngine2::CauseBreak | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fa0d559887019a697b820a5a6c91f80b78c6b713
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920951"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Запросы, что все программы, отлаживаемой, этот модуль отладки (DE), чтобы остановить выполнение следующего, один из своих потоков пытается выполнить.

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
 Этот метод является асинхронным: [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) событие отправляется, когда программа затем пытается выполнить после вызова этого метода.

## <a name="see-also"></a>См. также
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)