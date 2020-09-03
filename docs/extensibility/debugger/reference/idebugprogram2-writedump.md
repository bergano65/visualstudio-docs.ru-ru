---
title: 'IDebugProgram2:: Вритедумп | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722737"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Записывает дамп в файл.

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
окне Значение из перечисления [думптипе](../../../extensibility/debugger/reference/dumptype.md) , указывающее тип дампа, например short или long.

`pszDumpUrl`\
окне URL-адрес для записи дампа. Как правило, он имеет вид `file://c:\path\filename.ext` , но может быть любым допустимым URL-адресом.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Дамп программы обычно включает текущий кадр стека, стек, список потоков, выполняющихся в программе, и, возможно, любой объем памяти, который владеет программой.

## <a name="see-also"></a>См. также раздел
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
