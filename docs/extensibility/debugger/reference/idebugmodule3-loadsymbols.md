---
title: IDebugModule3::LoadSymbols | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9068eed8881124e75f06f4b97d3430ff3ef80e8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918684"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Загрузка символов для текущего модуля.

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
 Если метод завершается успешно, возвращается `S_OK`. Если происходит сбой, он возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод загружает символы из текущего пути поиска (который может быть изменен путем вызова [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) метод).

 Этот метод является предпочтительным, чем [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) метод.

## <a name="see-also"></a>См. также
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)