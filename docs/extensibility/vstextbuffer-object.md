---
title: Объект VSTextBuffer Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ea44d2b22c96d49f334f2ea33f9db8d69b5eb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697729"
---
# <a name="vstextbuffer-object"></a>Объект VSTextBuffer
Объект буфера текста представляет собой поток текста Unicode, который обычно ассоциируется с файлом. Объект <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> может использоваться вне контекста основного редактора, как в мастере.

 В следующей таблице показаны интерфейсы `VSTextBuffer`.

|Метод|Описание|
|------------|-----------------|
|[Iolecommandtarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Стандартный OLE-интерфейс. Используется для отменить/переделать обработку в буфере.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Стандартный OLE-интерфейс.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Стандартный OLE-интерфейс.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Позволяет создавать действия соединений (т.е. действия, сгруппированные в единую единицу отменить/переделать).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Обеспечивает сохранение данных документов, управляемых текстовым буфером.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Предоставляет базовые услуги; используется многими клиентами.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Используется для поиска буфера.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Обеспечивает возможности чтения и записи с помощью двухмерных координат. Наследует от `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Обеспечивает возможности чтения и записи с помощью одномерных координат. Наследует от `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Обеспечивает быстрый, ориентированный на поток, последовательный доступ к тексту в буфере.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Обеспечивает доступ к общей коллекции свойств. Наиболее важным свойством является имя или прозвище буфера. Вы можете хранить свои собственные случайные данные в буфере с помощью этого интерфейса, создавая GUID и используя его в качестве ключа.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Поддерживает точки соединения для событий.|

## <a name="remarks"></a>Примечания
 Это, `VSTextBuffer` как правило, найти по вызову `QueryInterface` на `IVsTextBuffer`. Для получения дополнительной информации [см.](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015)

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Цифры отодвите](https://www.microsoft.com/download/details.aspx?id=55984)
