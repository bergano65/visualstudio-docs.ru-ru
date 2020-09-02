---
title: 'IDebugBinder3:: Финдалиас | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a697e39d21b1c25a98c09ad6cc4837cca7a293
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735861"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Этот метод находит псевдоним по заданному имени. При этом будут искаться все псевдонимы в программе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Параметры
`pcstrName`\
окне Имя искомого псевдонима.

`ppAlias`\
заполняет Найден псевдоним (если имеется), представленный интерфейсом [идебугалиас](../../../extensibility/debugger/reference/idebugalias.md) .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает значение `S_FALSE` (если псевдоним не найден) или код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод инициализирует целевой объект до значения null перед вызовом метода; После этого проверяется наличие значения NULL, чтобы определить, был ли найден псевдоним.

## <a name="see-also"></a>См. также раздел
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
