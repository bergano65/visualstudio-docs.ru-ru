---
title: 'IDebugProcess2:: Кандетач | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 06cad6406951467339d34e467c6de3677cda724a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874169"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
Определяет, может ли диспетчер отладки сеанса (SDM) отсоединить процесс.

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
 В случае успеха возвращает значение, `S_OK.` `S_FALSE` Если отладчик не может отсоединиться от процесса. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
