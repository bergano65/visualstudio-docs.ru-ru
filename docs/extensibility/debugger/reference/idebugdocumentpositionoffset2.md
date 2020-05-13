---
title: IDebugДокументОпозицияСтекти2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d967ec9cf406f7dae691c3f05eda514e0907c7e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731598"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Представляет позицию в исходном файле в качестве смещения символов.

## <a name="syntax"></a>Синтаксис

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Реализовано IDE и потребляется двигателями отладки.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugDocumentPositionOffset2`.

|Метод|Описание|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Извлекает диапазон для текущего положения документа.|

## <a name="remarks"></a>Примечания
 Это возвращает ту же информацию, что и [GetRange,](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) но в `char` смещениях с начала документа. В нем представлен документ, как будто он будет существовать на диске, т.е. одномерный массив символов, а не информация о строке и столбце, которая обычно возвращается.

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
