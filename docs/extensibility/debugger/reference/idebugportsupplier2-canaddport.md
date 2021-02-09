---
title: 'IDebugPortSupplier2:: Канаддпорт | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ebd90baebc859f340bfb06df3fdbdc6012588183
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904567"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Проверяет, может ли поставщик порта добавлять новые порты.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>Возвращаемое значение
 Если порт можно добавить, возвращает значение `S_OK` ; в противном случае возвращается значение, `S_FALSE` указывающее, что порты не могут быть добавлены к этому поставщику портов.

## <a name="remarks"></a>Remarks
 Вызовите этот метод перед вызовом метода [аддпорт](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) , так как последний метод создает порт, а также добавляет его, что может занять много времени.

## <a name="see-also"></a>См. также раздел
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
