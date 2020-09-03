---
title: 'Идебугпортпиккер:: SetSite | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 07dac3f407b6869dad90f06d778911fdd9cfed41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724868"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Задает поставщик служб.

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
окне Ссылка на интерфейс поставщика услуг.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод будет вызываться до вызова любых других методов.

## <a name="see-also"></a>См. также раздел
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
