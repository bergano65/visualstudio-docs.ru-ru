---
title: 'Иенумдебугфиелдс:: Clone | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Clone
helpviewer_keywords:
- IEnumDebugFields::Clone method
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5657e5db99bd062fa16aae9f9d8516bdbabc99f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727698"
---
# <a name="ienumdebugfieldsclone"></a>IEnumDebugFields::Clone
Этот метод возвращает копию текущего перечисления в виде отдельного объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Clone(
   IEnumDebugFields** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
заполняет Возвращает копию этого перечисления в виде отдельного объекта.

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Копия перечисления имеет то же состояние, что и оригинал, во время вызова этого метода. Однако исходное состояние копии и исходного состояния является отдельным и может быть изменено по отдельности.

## <a name="see-also"></a>См. также
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)