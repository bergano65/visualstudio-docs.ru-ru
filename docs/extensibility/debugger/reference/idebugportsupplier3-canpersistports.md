---
title: IDebugPortSupplier3::CanPersistPorts | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11bc6e21e8b70a5bd95c001f4173a7da3f3fe4be
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340073"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Этот метод определяет ли поставщик порта может сохранять данные порты (при их записи на диск) между вызовами отладчика.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Параметры
 Отсутствует.

## <a name="return-value"></a>Возвращаемое значение
 `S_OK` Если порты могут сохраняться, или `S_FALSE` для указания, что порты не могут быть сохранены.

## <a name="remarks"></a>Примечания
 Если поставщика порта можно сохранить порты, его следует сделать это, когда он будет уничтожен и затем загружает их повторно при создании еще раз для экземпляра.

## <a name="see-also"></a>См. также
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)