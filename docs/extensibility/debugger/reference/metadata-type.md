---
title: METADATA_TYPE Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714286"
---
# <a name="metadata_type"></a>METADATA_TYPE
Эта структура определяет информацию о типе поля, взятом из метаданных.

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
 Id приложения, из которого пришел символ. Это используется для однозначной идентификации экземпляра приложения.

 `guidModule`\
 GUID модуля, содержащего это поле.

 `tokClass`\
 Идентификатор маркера метаданных этого типа.

 (К) `_mdToken` является `typedef` для 32-битного `int`.

## <a name="remarks"></a>Примечания
 Эта структура появляется как часть соединения в `dwKind` [структуре TYPE_INFO,](../../../extensibility/debugger/reference/type-info.md) когда `TYPE_KIND_METADATA` поле `TYPE_INFO` структуры устанавливается (значение из [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) перечисления).

 Значение `tokClass` представляет собой маркер метаданных, который однозначно идентифицирует тип. Подробную информацию о том, как интерпретировать верхние фрагменты идентификатора метаданных, можно узнать `CorTokenType` в файле corhdr.h в SDK .NET Framework.

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
