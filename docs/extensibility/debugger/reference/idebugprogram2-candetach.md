---
title: IDebugProgram2::CanDetach | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc95cee8a463337564ddfec5322ab074e3485bc1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693608"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Определяет, если отладчик (DE) можно отсоединить от программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Возвращаемое значение
 Если можно будет отсоединить, возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `S_FALSE` Если DE не удается отсоединиться от программы.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)