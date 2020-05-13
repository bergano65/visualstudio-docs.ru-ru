---
title: Объект VSTextView (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81d5e02d6ec18f8561a83b414532a4b78def5c09
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697715"
---
# <a name="vstextview-object"></a>Объект VSTextView

Текстовое представление — это окно, которое позволяет пользователям просматривать и отсеивать текст буфера текста Unicode. По сути, представление является то, что большинство пользователей называют редактором. Поскольку представление отделено от буфера различными слоями текста (обертывание слов, описание текста и т.д.), представление не гарантируется точное представление текста в буфере. Для получения дополнительной информации о текстовом представлении [см. Доступ к представлению theText с помощью устаревшего API](/visualstudio/extensibility/accessing-thetext-view-by-using-the-legacy-api?view=vs-2015).

В следующей таблице показаны <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> интерфейсы объекта.

|Интерфейс|Описание|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Стандартный OLE-интерфейс.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Стандартный OLE-интерфейс.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Стандартный OLE-интерфейс.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Стандартный OLE-интерфейс.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Позволяет создавать сложные действия (т.е. действия, сгруппированные в единую единицу отменить/переделать).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Предоставляет основные методы управления и доступа к представлению. `IVsTextView`не резьбовые безопасно.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Создает и управляет оконным стеклом.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Взаимодействует со слоями текста.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Выполняет операции на представлении из другого потока.|

## <a name="see-also"></a>См. также

- [Цифры отодвите](https://www.microsoft.com/download/details.aspx?id=55984)
- [Объект VSTextBuffer](../extensibility/vstextbuffer-object.md)
