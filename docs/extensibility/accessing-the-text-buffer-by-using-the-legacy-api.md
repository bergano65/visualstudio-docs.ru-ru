---
title: "Доступ к текстовый буфер с помощью API прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - текстовых буферов"
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Доступ к текстовый буфер с помощью API прежних версий
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Текст отвечает за управление текстовые потоки и сохранение файла.  Хотя буфер может считывать или записывать все другие форматы, обычное сообщение с буфером выполняется с помощью Юникода.  В традиционных API, текстовый буфер может использовать либо одно или плоская система координат для определения расположения символа в буфере.  
  
## Системы координат одной и 2\-Измерения  
 Одноразмерная координат позиция основана на позиции знака из первого символа в буфере, например 147.  Использовании <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> интерфейс для доступа к одномерный массив расположение в буфере.  Плоская система координат основан на парах линии и индексов.  Например, символ в буфере, с 43, 5 был бы на линии 43 5 символов справа от первого символа в этой линии.  Доступ к плоское расположение в буфере с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> интерфейс.  Оба <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> и  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> интерфейсы реализуются объектом текстового буфера \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>\) и может быть друг от друга с помощью  `QueryInterface`.  На следующей диаграмме показаны эти и другие интерфейсы ключа on <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 ![Объект текстового буфера](../extensibility/media/vstextbuffer.png "vsTextBuffer")  
Объект текстового буфера  
  
 Хотя любая система координат работает в текстовом буфере, она оптимизирована для использования плоских координат.  Одноразмерная система координат может создать снижение производительности.  Поэтому используйте плоскую систему координат, когда это возможно.  
  
 Обязанностью второго текстового буфера сохранение файла.  Чтобы сделать это, реализующий объект текстового буфера <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> и действует как компонент объекта данных документа для элементов проекта и других компонентов среды, участвующих в сохраняемости.  Дополнительные сведения см. в разделе [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md).  
  
## Содержание  
 [Изменение параметров представления с помощью API прежних версий](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Объясняется, как изменить параметры представления с помощью API прежних версий.  
  
 [С помощью диспетчера текст для наблюдения за глобальные параметры](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Объясняет, как использовать диспетчер текста для мониторинга глобальные параметры.  
  
## См. также  
 [В редакторе ядра](../extensibility/inside-the-core-editor.md)