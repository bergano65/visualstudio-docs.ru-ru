---
title: IDebugProgram2::WriteDump | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 90d9d680ca83967f9f651269e186670fb90a771d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343634"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Записывает в файл дампа.

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
[in] Значение из [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) перечисление, указывающее тип дампа, например, short или long.

`pszDumpUrl`\
[in] Записываются в URL-адрес. Как правило, это в виде `file://c:\path\filename.ext`, но может быть любой допустимый URL-адрес.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Программа дампа обычно будет включать текущий кадр стека, сам стек, список потоков, выполняющих в программы и возможно, программа, которой принадлежит память.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)