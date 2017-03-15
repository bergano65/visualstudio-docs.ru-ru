---
title: "В редакторах синтаксиса | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] пользовательский – Цветовая подсветка синтаксиса"
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# В редакторах синтаксиса
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Редакторы пакет SDK для среды Visual Studio, в том числе редактором, используют языковой службы, чтобы определить конкретные синтаксических элементов, и отобразить их с указанными цветами для данного представления документа.  
  
## Требования к колоризации  
 Все редакторы, реализующий colorizer языковой службы.  
  
1.  Используйте реализация объекта <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> управление текст, который необходимо colorized и реализация объекта  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> представления рисования текста.  
  
2.  Получите интерфейс к определенной службе языка, запрашивая поставщиков услуг VSPackage, используя идентификатор GUID службы языков, определяющий.  
  
3.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> метод реализации объекта  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  Этот метод связывает службу языка с <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> реализация которой VSPackage использует для управления текст, который должен colorized.  
  
## Потребление основные Colorizer службы языка редактора  
 Когда служба языка с colorizer получена экземпляром редактора, анализа и отображения текста colorizer языковой службы происходят автоматически, без необходимости любой более добавочной вмешательства со стороны пользователя.  
  
 Интегрированная среда разработки явным образом:  
  
-   Вызывает colorizer, необходимыми для синтаксического анализа и анализа текста, так как оно добавляется или изменяется в реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  
  
-   Обеспечивает отображение предоставленный представлением документа, предоставленных <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> реализация обновления и обновления, используя сведения, возвращаемые методом colorizer.  
  
## Потребление редактора Non\-сердечника Colorizer службы языка  
 Экземпляры редактора Non\-сердечника также могут использовать службу колоризации синтаксиса языковой службы, но они должны явно получить и применить colorizer службы и обновлять их документ обзор.  
  
 Для этого требуется редактора non\-сердечника:  
  
1.  Получите объект colorizer языковой службы \(который реализует `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` и  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>\).  В VSPackage делает это путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> метод в интерфейсе языковой службы.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод, чтобы запросить был colorized указанный диапазон текста.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод возвращает массив значений, по одному для каждого символа в colorized объеме текста.  Он также определяет диапазон текста, что и заданный тип цветного элемента, в виде комментария, ключевое слово и тип данных.  
  
3.  Используйте сведения о колоризации возвращаемые by <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> обновление и отображения его текст.  
  
> [!NOTE]
>  В дополнение к использованию colorizer языковой службы, VSPackage может выбрать для использования общецелевого механизма текст\-расцветки пакет SDK для среды Visual Studio.  Дополнительные сведения об этом механизме см. в разделе [Шрифты и цвета](../extensibility/using-fonts-and-colors.md).  
  
## См. также  
 [Синтаксиса в языковую службу для прежних версий](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Реализация Цветовая подсветка синтаксиса](../extensibility/internals/implementing-syntax-coloring.md)   
 [Практическое руководство: использование встроенных цветных элементов](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Пользовательские цветных элементов](../extensibility/internals/custom-colorable-items.md)