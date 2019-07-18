---
title: IDebugPortPicker::SetSite | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33d6d12bd21a6ab208fed019c1e0f763bce86724
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340348"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Задает поставщик службы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetSite(
   IServiceProvider * pSP
);
```

```csharp
public int SetSite(
   IServiceProvider pSP
);
```

## <a name="parameters"></a>Параметры
`pSP`\
[in] Ссылка на интерфейс поставщика службы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод будет вызываться до вызова всех остальных методов.

## <a name="see-also"></a>См. также
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)