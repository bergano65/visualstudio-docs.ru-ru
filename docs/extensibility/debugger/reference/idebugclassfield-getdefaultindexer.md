---
title: IDebugClassField::GetDefaultIndexer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eaaddbe6bb223e8e2987f8310f1d8e08d5602a01
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206834"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
Получает имя индексатора по умолчанию.

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
`pbstrIndexer` [out] Возвращает строку, содержащую имя индексатора по умолчанию.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK, или возвращает S_FALSE, если нет индексатора по умолчанию. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Индексатор по умолчанию класса — свойство, которое помечается как `Default` свойство для обращений к массива. Это относится к [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]. Ниже приведен пример индексатор по умолчанию, объявленные в [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] и способах ее использования.

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