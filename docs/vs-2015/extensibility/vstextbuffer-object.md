---
title: Объект VSTextBuffer | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 987514f20746b8480391a35d7a9c9a9d3663cac2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728784"
---
# <a name="vstextbuffer-object"></a>Объект VSTextBuffer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Объект текстового буфера представляет поток текста в формате Юникод, который связан с файлом. Объект <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект может использоваться вне контекста базового редактора, как в случае мастер.  
  
 В следующей таблице показаны интерфейсы `VSTextBuffer`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|Стандартный OLE-интерфейс. Главным образом используется для обработки в буфере отмены и повтора.|  
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

