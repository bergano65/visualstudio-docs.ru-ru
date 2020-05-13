---
title: IDebugProgram2::WriteDump Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 333535a727d88f66346ba4c94cb08b4917b8acfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722737"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Записывает свалку в файл.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WriteDump( 
   DUMPTYPE  DumpType,
   LPCOLESTR pszDumpUrl
);
```

```csharp
int WriteDump( 
   enum_DUMPTYPE  DumpType,
   string         pszDumpUrl
);
```

## <a name="parameters"></a>Параметры
`DumpType`\
(в) Значение из перечисления [DUMPTYPE,](../../../extensibility/debugger/reference/dumptype.md) которое определяет тип дампа, например, короткий или длинный.

`pszDumpUrl`\
(в) URL-адрес для записи дампа. Как правило, это в `file://c:\path\filename.ext`виде, но может быть любой действительный URL.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Дамп программы обычно включает текущий кадр стека, сам стек, список потоков, работающих в программе, и, возможно, любую память, которой владеет программа.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
