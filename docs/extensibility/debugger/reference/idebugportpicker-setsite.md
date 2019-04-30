---
title: IDebugPortPicker::SetSite | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0964c94334ca0815b4410f6858dca5502b2f8a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918160"
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

#### <a name="parameters"></a>Параметры
 `pSP`

 [in] Ссылка на интерфейс поставщика службы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод будет вызываться до вызова всех остальных методов.

## <a name="see-also"></a>См. также
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)