---
title: BUILT_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09f0438bed235729d390b784725b89abec201c7f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693533"
---
# <a name="builttype"></a>BUILT_TYPE
Эта структура указывает сведения о типом поля, взятое из метаданных.

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

#### <a name="parameters"></a>Параметры
ulAppDomainID идентификатор приложения, от которого поступило символа. Это используется для уникальной идентификации экземпляра приложения.

guidModule идентификатор GUID модуля, содержащего это поле.

pUnderlyingField [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) идентифицирующий базового поля, связанные с этим полем построения.

## <a name="remarks"></a>Примечания
Эта структура является частью объединения в [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) структуры, когда `dwKind` поле `TYPE_INFO` структура присваивается `TYPE_KIND_BUILT` (значение из [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Перечисление).

## <a name="requirements"></a>Требования
Заголовок: sh.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
