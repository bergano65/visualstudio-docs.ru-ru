---
title: Объект VSTextBuffer | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e763b8006dd2c01f8e2ee4beeffa7c78100b15b3
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586310"
---
# <a name="vstextbuffer-object"></a>Объект VSTextBuffer
Объект текстового буфера представляет поток текста в формате Юникод, который связан с файлом. Объект <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект может использоваться вне контекста базового редактора, как показано в мастер.  
  
 В следующей таблице показаны интерфейсы `VSTextBuffer`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|Стандартный OLE-интерфейс. Используется для обработки в буфере отмены и повтора.|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Стандартный OLE-интерфейс.|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|Стандартный OLE-интерфейс.|  
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
 [Изменение фигур](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)