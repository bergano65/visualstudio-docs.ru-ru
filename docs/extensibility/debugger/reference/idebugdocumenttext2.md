---
title: IDebugDocumentText2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: af72993a4a02ce7d25858bf3bd4f0690e0d30f5a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923106"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Этот интерфейс представляет текстовый документ.

## <a name="syntax"></a>Синтаксис

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс, когда исходный код, который он должен предоставить, находится в текстовой форме. Так как это наиболее типичный случай, если метод DE реализует интерфейс [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , он также должен реализовать `IDebugDocumentText2` интерфейс.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Используйте `QueryInterface` метод для получения этого интерфейса из `IDebugDocument2` интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Помимо методов `IDebugDocument2` интерфейса, этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Получает размер текста в данной позиции в документе.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Извлекает текст из указанной позицией в документе.|

## <a name="remarks"></a>Remarks
 Объект, реализующий этот интерфейс, должен также реализовать <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> интерфейс, который предоставляет <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> интерфейс для объекта [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
