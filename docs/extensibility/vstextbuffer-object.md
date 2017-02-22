---
title: "Объект VSTextBuffer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTextBuffer"
helpviewer_keywords: 
  - "Объект VSTextBuffer, справочник"
  - "представления [Visual Studio SDK] VSTextBuffer объекта"
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Объект VSTextBuffer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Объект текстового буфера представляет поток текста в формате Юникод, который связан с файлом. Объект <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект можно использовать вне контекста базового редактора в случае мастер.  
  
 В следующей таблице показаны интерфейсы `VSTextBuffer`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|Стандартный интерфейс OLE. В основном используется для обработки в буфере отмены или повтора.|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Стандартный интерфейс OLE.|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|Стандартный интерфейс OLE.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Позволяет создавать составные действия \(действия, сгруппированные в единое одной отмены или повтора\).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Обеспечивает сохранность данных документа под управлением текстового буфера.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Предоставляет базовые службы; используется многими клиентами.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Используется для поиска буфера.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Обеспечивает чтение и запись возможности с помощью двухмерные координаты. Наследует от `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Обеспечивает чтение и запись возможности с помощью одномерный массив координат. Наследует от `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Обеспечивает быстрый, поточно ориентированными, последовательный доступ к текста в буфере.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Предоставляет доступ к общей коллекции свойств. Наиболее важным свойством является имя или моникера буфера. Случайные данные можно сохранить в буфере, с помощью этого интерфейса, создать GUID и использовать его в качестве ключа.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Поддерживает точки подключения для событий.|  
  
## Заметки  
 `VSTextBuffer` Обычно находится по `QueryInterface` вызвать `IVsTextBuffer`. Дополнительные сведения см. в разделе [Текстовый буфер](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Figures Edit](http://msdn.microsoft.com/ru-ru/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)