---
title: IDebugДокументТекст2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b5def7f6cc4ac5ced91ca0a273ce750003dca20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731559"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Этот интерфейс представляет собой текстовый документ.

## <a name="syntax"></a>Синтаксис

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Отладка двигателя (DE) реализует этот интерфейс, когда исходный код, необходимый для поставки в текстовой форме. Так как это наиболее типичный случай, если DE реализует интерфейс [IDebugDocument2,](../../../extensibility/debugger/reference/idebugdocument2.md) он также должен реализовать `IDebugDocumentText2` интерфейс.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Используйте `QueryInterface` метод, чтобы получить `IDebugDocument2` этот интерфейс из интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам `IDebugDocument2` на интерфейсе, этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Извлекает размер текста в этой позиции в документе.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Извлекает текст из указанной позиции в документе.|

## <a name="remarks"></a>Примечания
 Объект, реализуемый в <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> этом интерфейсе, должен также реализовать интерфейс, который предоставляет <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> интерфейс для объекта [IDebugDocumentTextEvents2.](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
