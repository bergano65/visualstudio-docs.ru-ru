---
title: IDebugDocumentPositionOffset2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3793d54249fca1dc867cfe4072326245a67852cb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333271"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Представляет позицию в файле исходного кода как смещение в буфере символов.

## <a name="syntax"></a>Синтаксис

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Реализуется интегрированной среды разработки и потребляемых отладчиков.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugDocumentPositionOffset2`.

|Метод|Описание|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Извлекает диапазон для текущей позиции документа.|

## <a name="remarks"></a>Примечания
 Возвращает те же сведения, что [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) в `char` смещений от начала документа. Это представляет документ, как он будет существовать на диске, то есть в одномерный массив символов, а не сведения строки и столбца, который обычно возвращается.

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)