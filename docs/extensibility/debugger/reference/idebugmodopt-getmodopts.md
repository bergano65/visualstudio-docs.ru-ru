---
title: IDebugModOpt::GetModOpts Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ab870db3ae3517b60bebd4815e4530f6035b327
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727047"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Извлекает список дополнительных модификаторов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetModOpts(
   ULONG  celt,
   BSTR*  rgelt,
   ULONG* pceltFetched
);
```

```csharp
int GetModOpts(
   uint         celt,
   out string[] rgelt,
   ref uint     pceltFetched
);
```

## <a name="parameters"></a>Параметры
`celt`\
(в) Количество элементов, которые будут возвращены.

`rgelt`\
(ваут) Возвращает массив, содержащий параметры.

`pceltFetched`\
(в, вне) Количество элементов, `rgelt` возвращенных в массив.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
