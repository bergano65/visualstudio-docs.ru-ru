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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5d0c67d62f57076f29f2c2ef60d456f517ae97fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724744"
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
