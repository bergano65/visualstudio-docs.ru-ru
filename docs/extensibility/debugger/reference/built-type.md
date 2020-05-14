---
title: BUILT_TYPE Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 885f17b0841a39672c87be5bc7c947b2e0d9c7e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737696"
---
# <a name="built_type"></a>BUILT_TYPE
Эта структура определяет информацию о типе поля, взятом из метаданных.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagTYPE_BUILT {
    ULONG32      ulAppDomainID;
    GUID         guidModule;
    IDebugField* pUnderlyingField;
} BUILT_TYPE;
```

```csharp
public struct BUILT_TYPE {
    public uint        ulAppDomainID;
    public Guid        guidModule;
    public IDebugField pUnderlyingField;
};
```

## <a name="members"></a>Участники
`ulAppDomainID`\
Id приложения, из которого пришел символ. Это используется для однозначной идентификации экземпляра приложения.

`guidModule`\
GUID модуля, содержащего это поле.

`pUnderlyingField`\
Объект [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) идентифицирующий основное поле, связанное с этим построенным полем.

## <a name="remarks"></a>Примечания
Эта структура появляется как часть соединения в `dwKind` [структуре TYPE_INFO,](../../../extensibility/debugger/reference/type-info.md) когда `TYPE_KIND_BUILT` поле `TYPE_INFO` структуры устанавливается (значение из [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) перечисления).

## <a name="requirements"></a>Требования
Заголовок: sh.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
