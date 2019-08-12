---
title: Объект Встекствиев | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5d3983dcefd515a43d573166c9bd772fd23bf0a
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68924157"
---
# <a name="vstextview-object"></a>Объект Встекствиев
Текстовое представление — это окно, которое позволяет пользователям просматривать и изменять текст в Юникоде для текстового буфера. По сути, представление — это то, что большинство пользователей ссылается на редактор. Так как представление отделяется от буфера различными текстовыми слоями (перенос по словам, структурирование текста и т. д.), представление не обязательно должно быть точным представлением текста в буфере. Дополнительные сведения о представлении текста см. в разделе [доступ к представлению сетекст с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md).

 В следующей таблице показаны интерфейсы в <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объекте.

|Интерфейс|Описание|
|---------------|-----------------|
|[идропсаурце](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Стандартный интерфейс OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Стандартный интерфейс OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Стандартный интерфейс OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Стандартный интерфейс OLE.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Позволяет создавать составные действия (то есть действия, сгруппированные в одну единицу отмены или возврата).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Предоставляет базовые методы для управления представлением и доступа к ним. `IVsTextView`не является потокобезопасным.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Создает и управляет областью окна.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Взаимодействует с текстовыми слоями.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Выполняет операции с представлением из другого потока.|

## <a name="see-also"></a>См. также
- [Изменение фигур](https://www.microsoft.com/download/details.aspx?id=55984)
- [Объект Встекстбуффер](../extensibility/vstextbuffer-object.md)
- [Доступ к представлению Сетекст с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)