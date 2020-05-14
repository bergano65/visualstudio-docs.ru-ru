---
title: IDebugModule3::LoadSymbols Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c61339305200acc9a6c572a1a96595dc4cb6f50
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726775"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Загружает символы для текущего модуля.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT LoadSymbols(
   void
);
```

```csharp
int LoadSymbols();
```

## <a name="return-value"></a>Возвращаемое значение
 Если метод завершается успешно, возвращает значение `S_OK`. В противном случае функция возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод загружает символы из текущего пути поиска (который может быть изменен, вызывая метод [SetSymbolPath).](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)

 Этот метод является предпочтительным по сравнению с [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) методом.

## <a name="see-also"></a>См. также
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
