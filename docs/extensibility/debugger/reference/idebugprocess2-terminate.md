---
title: IDebugProcess2::Terminate | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Terminate
helpviewer_keywords:
- IDebugProcess2::Terminate
ms.assetid: 5e6bf373-0fe9-4321-b04a-473a65f664d9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 704f2b59852a47b02dcf5d6bdaa60e05ca722ca0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703569"
---
# <a name="idebugprocess2terminate"></a>IDebugProcess2::Terminate
Завершает процесс.

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
 По завершении процесса завершаются все программы, в рамках этого процесса; Нет разрешено запускать любой дополнительный код.

## <a name="see-also"></a>См. также
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)