---
title: IDebugProgram2::Прекращение Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 913c90e34e308ce5bb4ceecface739afc8d03f3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722743"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Прекращает программу.

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
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Если это возможно, программа будет прекращена и выгружена из процесса; в противном случае, отладка двигателя (DE) будет выполнять любые необходимые очистки.

 Этот метод или метод [«Прекращение»](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) вызывается IDE, как правило, в ответ на то, что пользователь останавливает все отладки. Реализация этого метода должна, в идеале, прекратить программу в рамках процесса. Если это невозможно, DE должен предотвратить запуск программы в этом процессе (и сделать любую необходимую очистку). Если `IDebugProcess2::Terminate` метод был вызван IDE, весь процесс будет завершен через `IDebugProgram2::Terminate` некоторое время после вызова метода.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Завершить](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
