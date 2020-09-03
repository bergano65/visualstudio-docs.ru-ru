---
title: METADATA_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afe5ea128775c7be0e48035ab4c7e7d370c9d233
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714286"
---
# <a name="metadata_type"></a>METADATA_TYPE
Эта структура задает сведения о типе поля, взятого из метаданных.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagTYPE_METADATA {
   ULONG32  ulAppDomainID;
   GUID     guidModule;
   _mdToken tokClass;
} METADATA_TYPE;
```

```csharp
public struct METADATA_TYPE {
   public uint ulAppDomainID;
   public Guid guidModule;
   public int  tokClass;
};
```

## <a name="parameters"></a>Параметры
 `ulAppDomainID`\
 Идентификатор приложения, от которого получен символ. Используется для уникальной идентификации экземпляра приложения.

 `guidModule`\
 Идентификатор GUID модуля, содержащего это поле.

 `tokClass`\
 Идентификатор маркера метаданных этого типа.

 [C++] `_mdToken` — `typedef` для 32-разрядного `int` .

## <a name="remarks"></a>Remarks
 Эта структура отображается как часть объединения в структуре [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) , если `dwKind` поле `TYPE_INFO` структуры имеет `TYPE_KIND_METADATA` значение (Value из перечисления [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).

 `tokClass`Значение является маркером метаданных, уникальным образом определяющим тип. Дополнительные сведения о том, как интерпретировать верхние биты идентификатора маркера метаданных, см. в описании `CorTokenType` перечисления в файле корхдр. h в пакете SDK .NET Framework.

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
