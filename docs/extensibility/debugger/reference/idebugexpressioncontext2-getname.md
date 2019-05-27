---
title: IDebugExpressionContext2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1961ac778dab2d17a87748cae8e1210f6b13422d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66201064"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
Извлекает имя в контекст оценки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName( 
   out string pbstrName
);
```

## <a name="parameters"></a>Параметры
`pbstrName`\
[out] Возвращает имя контекста вычисления.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Имя — это описание этого контекста вычисления. Она обычно является то, что может быть проанализирован вычислитель выражений, который ссылается на этот контекст точные оценки. Например в C++ имя выглядит следующим образом:

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>См. также
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)