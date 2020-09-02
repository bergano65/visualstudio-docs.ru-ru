---
title: 'IDebugExpressionEvaluator2:: "Услуга" | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5428606ad54c7938037c3ffecf04f1cfe41787c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729348"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Извлекает объект службы по заданному уникальному идентификатору.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetService (
   GUID        uid,
   IUnknown ** ppService
);
```

```csharp
int GetService (
   Guid       uid,
   out object ppService
);
```

## <a name="parameters"></a>Параметры
`uid`\
окне Уникальный идентификатор получаемой службы.

`ppService`\
заполняет Возвращает объект, представляющий службу.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот механизм может использоваться сторонним средством оценки выражений для получения служб от другого средства оценки выражений. Например, этот метод можно использовать для получения интерфейса для службы визуализатора из вычислителя выражений по умолчанию. Средствам оценки выражений сторонних производителей вряд ли придется реализовывать этот интерфейс.

## <a name="see-also"></a>См. также раздел
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
