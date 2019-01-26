---
title: Объект VSTextBuffer | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d526156a07ba66d01ca86fb39daaaedf73d3bf2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990022"
---
# <a name="vstextbuffer-object"></a>Объект VSTextBuffer
Объект текстового буфера представляет поток текста в формате Юникод, который связан с файлом. Объект <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект может использоваться вне контекста базового редактора, как показано в мастер.  
  
 В следующей таблице показаны интерфейсы `VSTextBuffer`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Стандартный OLE-интерфейс. Используется для обработки в буфере отмены и повтора.|  
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Стандартный OLE-интерфейс.|  
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Стандартный OLE-интерфейс.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Позволяет создавать действия соединения (то есть действия, сгруппированные в блок одной отмены и повтора).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Включает сохранение данных документа, управляемых текстовым буфером.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Предоставляет базовые службы; Многие клиенты используют.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Используется для поиска в буфер.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Предоставляет возможности, используя двухмерные координаты чтения и записи. Наследует от `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Обеспечивает чтение и запись с помощью одноразмерных координат. Наследует от `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Обеспечивает быстрый, поточно ориентированный, последовательный доступ к текста в буфере.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Предоставляет доступ к общей коллекции свойств. Наиболее важным свойством является имя или моникер буфера. Случайные данные можно сохранить в буфере, с этим интерфейсом, создать GUID и использовать его в качестве ключа.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Поддерживает точки подключения для событий.|  
  
## <a name="remarks"></a>Примечания  
 `VSTextBuffer` Обычно находится по `QueryInterface` вызвать `IVsTextBuffer`. Дополнительные сведения см. в разделе [текстового буфера](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Изменение фигур](https://www.microsoft.com/download/details.aspx?id=55984)