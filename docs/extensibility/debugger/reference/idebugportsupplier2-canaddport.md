---
title: IDebugPortSupplier2::CanAddPort Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5d0c67d62f57076f29f2c2ef60d456f517ae97fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724744"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Проверяется, что поставщик порта может добавить новые порты.

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
 Если порт может быть `S_OK`добавлен, возвращается ; в противном случае возврат, `S_FALSE` указывающий на отсутствие портов, не может быть добавлен к этому поставщику порта.

## <a name="remarks"></a>Примечания
 Вызовите этот метод, прежде чем вызывать метод [AddPort,](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) так как последний метод создает порт, а также добавляйте его, что может занять много времени.

## <a name="see-also"></a>См. также
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
