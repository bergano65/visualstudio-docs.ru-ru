---
title: IDebugReference2::GetParent | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetParent
helpviewer_keywords:
- IDebugReference2::GetParent
ms.assetid: e3061665-ad3e-4c1b-b33f-82755fa21be3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a0e0b4995a6c7e01af955d672040ab81183c0f47
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66198800"
---
# <a name="idebugreference2getparent"></a>IDebugReference2::GetParent
Получает ссылку на родительский ссылку. Зарезервировано для будущего использования.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetParent ( 
   IDebugReference2** ppParent
);
```

```csharp
int GetParent ( 
   out IDebugReference2 ppParent
);
```

## <a name="parameters"></a>Параметры
`ppParent`\
[out] Возвращает [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объект, представляющий родительский элемент этого свойства.

## <a name="return-value"></a>Возвращаемое значение
 Всегда возвращает значение `E_NOTIMPL`.

## <a name="see-also"></a>См. также
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)