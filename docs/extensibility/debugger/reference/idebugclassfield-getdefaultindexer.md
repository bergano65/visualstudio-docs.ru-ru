---
title: IDebugClassField::GetDefaultIndexer Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 57e00107374485043af370967794bdade1c213d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734423"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
Получает имя индекса по умолчанию.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDefaultIndexer( 
   BSTR* pbstrIndexer
);
```

```csharp
int GetDefaultIndexer(
   out string pbstrIndexer
);
```

## <a name="parameters"></a>Параметры
`pbstrIndexer`(ваут) Возвращает строку, содержащую имя индекса по умолчанию.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращает S_OK или возвращает S_FALSE, если нет индекса по умолчанию. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Индексируемым по умолчанию класса — это `Default` свойство, которое помечено как свойство для доступа к массиву. Это характерно [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]для . Вот пример индекса по умолчанию, декларируемого в [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] и как он используется.

```vb
Imports System.Collections;

Public Class Class1
    Private myList as Hashtable

    Default Public Property Item(ByVal Index As Integer) As Integer
        Get
            Return CType(List(Index), Integer)
        End Get
        Set(ByVal Value As Integer)
            List(Index) = Value
        End Set
    End Property
End Class

Function GetItem(Index as Integer) as Integer
    Dim classList as Class1 = new Class1
    Dim value as Integer

    ' Access array through default indexer
    value = classList(2)

    ' Access array through explicit property
    value = classList.Item(2)

    Return value
End Function
```

## <a name="see-also"></a>См. также
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
