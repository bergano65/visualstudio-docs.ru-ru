---
title: 'IDebugEvent2:: OutAttribute | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64f4b404938143e5b1531798b1cded7ac6218de6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888281"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Возвращает атрибуты для данного события отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAttribute( 
   DWORD* pdwAttrib
);
```

```csharp
int GetAttribute( 
   out uint pdwAttrib
);
```

## <a name="parameters"></a>Параметры
`pdwAttrib`\
заполняет Сочетание флагов из перечисления [евентаттрибутес](../../../extensibility/debugger/reference/eventattributes.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) является общим для всех событий. Этот метод описывает тип события; Например, событие является синхронным или асинхронным и является событием остановки.

## <a name="see-also"></a>См. также раздел
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
