---
title: IDebugField::GetType | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetType
helpviewer_keywords:
- IDebugField::GetType method
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7eb0b6e17ccc7b95ec64449468469a85adfa8849
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212674"
---
# <a name="idebugfieldgettype"></a>IDebugField::GetType
Этот метод возвращает тип поля.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetType( 
   IDebugField** ppType
);
```

```csharp
int GetType(
   out IDebugField ppType
);
```

## <a name="parameters"></a>Параметры
`ppType`\
[out] Возвращает тип поля, что и другой [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объекта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)