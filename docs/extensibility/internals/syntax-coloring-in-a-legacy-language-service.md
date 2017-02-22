---
title: "Синтаксиса в языковую службу для прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "цветовая маркировка синтаксиса"
  - "языковые службы Цветовая подсветка синтаксиса"
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Синтаксиса в языковую службу для прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует службу расцветки для определения элементов языка, и отобразить их с указанными цветами в редакторе.  
  
## Модель Colorizer  
 Служба языков реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс, который затем используется редакторами.  Эта реализация отдельный объект от языковой службы, как показано на следующей иллюстрации.  
  
 ![График SVC Colorizer](../../extensibility/internals/media/figlgsvccolorizer.png "FigLgSvcColorizer")  
Простая модель colorizer  
  
> [!NOTE]
>  Служба расцветки отдельно от общего синтаксиса [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] механизм colorizing текста.  Дополнительные сведения о генералитете [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] colorizing механизма, поддерживающий см. в разделе  [Шрифты и цвета](../../extensibility/using-fonts-and-colors.md).  
  
 Кроме colorizer служба языка может предоставить пользовательские цветного элементы, используемые редактором путем объявления этого он содержит пользовательские элементы цветного.  Это можно сделать путем реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> интерфейс для одного и того же объекта, реализующего  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейс.  Он возвращает количество пользовательских цветного элементов, когда редактор вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> метод и возвращают отдельные пользовательский цветного элемента, когда редактор вызывает  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> метод.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> метод возвращает объект, который реализует  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> интерфейс.  Если языка 24 бита или значения высокого цвета, он должен реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейс на одном объекте как  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> интерфейс.  
  
## Использует службу языка Colorizer как VSPackage  
  
1.  VSPackage должно получить подходящую службу языка, которая требует служба языка VSPackage выполняет следующие действия:  
  
    1.  Используйте реализация объекта <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> интерфейс для получения текста colorized.  
  
         Текст обычно отображается с использованием объект, реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейс.  
  
    2.  Получает службу языка, запрашивая поставщиков услуг VSPackage для GUID языковой службы.  Языковой службы задаются в реестре расширением файла.  
  
    3.  Свяжите языковую службу с <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> путем вызова его  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> метод.  
  
2.  VSPackage может обращаться и использовать объект colorizer следующим образом:  
  
    > [!NOTE]
    >  VSPackages, которое использует редактор не должно получить базовые объекты colorizer языковой службы явным образом.  После того как экземпляр ядра возвращает соответствующую службу редактора языка, он выполняет все задачи колоризации показанные здесь.  
  
    1.  Получите объект colorizer языковой службы, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> и  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейсы, путем вызова  `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`метод в службе языка  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> объект.  
  
    2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод, чтобы получить данные colorizer для указанного диапазона текста.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> возвращает массив значений, по одному для каждого символа в colorized объеме текста.  Значения индексов цветного список элементов или цветного элемента по умолчанию список основных поддерживаемый редактором или пользовательский список цветного элемента, поддерживаемый службой языку самой.  
  
    3.  Используйте колоризации возвращаемые данные <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод для отображения выделенного текста.  
  
> [!NOTE]
>  В дополнение к использованию colorizer языковой службы, VSPackage также может использовать общего назначения [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] механизм расцветки текста.  Дополнительные сведения об этом механизме см. в разделе [Шрифты и цвета](../../extensibility/using-fonts-and-colors.md).  
  
## Содержание  
 [Реализация Цветовая подсветка синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md)  
 Содержит сведения о том, как редактор получает доступ к расцветка синтаксиса службы языка и языка служба должна реализовывать для поддержки расцветку синтаксиса.  
  
 [Практическое руководство: использование встроенных цветных элементов](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Демонстрирует, как использовать встроенные элементы из цветного языковой службы.  
  
 [Пользовательские цветных элементов](../../extensibility/internals/custom-colorable-items.md)  
 Описывает, как реализовать пользовательские цветного элементы.  
  
## См. также  
 [Шрифты и цвета](../../extensibility/using-fonts-and-colors.md)