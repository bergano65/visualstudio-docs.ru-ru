---
title: IDebugDocumentText2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6069b7c77995a855bfa47d1d369203f386b0302c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686877"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Этот интерфейс представляет текстовый документ.

## <a name="syntax"></a>Синтаксис

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Отладчик (DE) реализует этот интерфейс, когда исходный код, которым требуется предоставить в виде текста. Так как это наиболее распространенный случай, если реализует DE [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) интерфейс, он должен также реализовывать `IDebugDocumentText2` интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Используйте `QueryInterface` метод для получения этого интерфейса из `IDebugDocument2` интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам на `IDebugDocument2` интерфейс, этот интерфейс реализует следующие методы:

|Метод|Описание:|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Получает размер текста в этой позиции в документе.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Получение текста из указанной позиции в документе.|

## <a name="remarks"></a>Примечания
 Объект, реализующий этот интерфейс также необходимо реализовать <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> интерфейс предоставляет <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> интерфейс для [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) объекта.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)