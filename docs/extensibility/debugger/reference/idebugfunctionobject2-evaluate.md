---
title: IDebugFunctionObject2::Оценка Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d87d7d3531d198a1478b4aaa55b354c3ac101302
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728446"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Вызывает функцию и возвращает полученное значение в качестве объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Evaluate (
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwEvalFlags,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate (
   IDebugObject     ppParams,
   uint             dwParams,
   uint             dwEvalFlags,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Параметры
`ppParams`\
(в) Массив объектов [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) представляющий параметры ввода. Каждый из этих параметров был создан с помощью одного из методов создания в этом интерфейсе.

`dwParams`\
(в) Количество параметров в `ppParams` массиве.

`dwEvalFlags`\
(в) Комбинация флагов из перечисления [EVALFLAGS,](../../../extensibility/debugger/reference/evalflags.md) которые определяют, как должна выполняться оценка.

`dwTimeout`\
(в) Определяет максимальное время, в миллисекундах, чтобы ждать, прежде чем вернуться из этого метода. Используйте **INFINITE,** чтобы ждать бесконечно.

`ppResult`\
(ваут) Возвращает **IDebugObject,** представляющий значение функции как объекта.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
