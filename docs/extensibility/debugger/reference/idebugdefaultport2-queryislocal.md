---
title: 'IDebugDefaultPort2:: Куерислокал | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c06230f7bbd1825fe73a22f9b1fdc35aea35c499
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732324"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
Этот метод определяет, находится ли этот порт на локальном компьютере.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает, `S_OK` Если этот порт является локальным (на том же компьютере, что и вызывающий объект), или `S_FALSE` порт находится на другом компьютере.

## <a name="see-also"></a>См. также раздел
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
