---
title: "Раскрывающийся список | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних - раскрывающемся списке панели"
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Раскрывающийся список
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Линейчатая диаграмма предоставляется раскрывающемся списке в верхней части окна кода и содержит 2 раскрывающегося списка.  
  
## Раскрывающиеся полосы интерфейсы  
 IN [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)]например, черта, раскрывающемся списке, содержащий списки  [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] элементы и  [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] Функции\-члены элементов, как показано на рисунке ниже.  
  
 ![Раскрывающиеся строки](~/extensibility/media/vsdropdown_bar.gif "vsDropdown\_bar")  
Список линейчатых диаграмм  
  
 При реализации черта раскрывающемся списке, 4 интерфейса первичной серьезности:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Реализуйте этот интерфейс, чтобы вставить содержимое полосы раскрывающегося списка.  Каждое сочетание список может содержать обычный текст или причудливое текст \(полужирный, курсив, подчеркивание или\), может иметь расцветку шрифта. для текста окна или затенены расцветку шрифта и может при необходимости предоставить меньшее растровое изображение вниз рядом с элементом падающим.  Аналогично <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> интерфейс, образы растрового изображения предоставляется в списках образа.  Каждое сочетание список может иметь разные списки завершения образа. однако каждый список образа должен содержать образы ту же высоту.  Кроме того, использование <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> метод, можно предоставить подсказку для каждого сочетания.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Вызовите этот интерфейс или создайте линейчатую диаграмму или уничтожить раскрывающемся списке для окна кода.  Этот интерфейс может также использоваться для определения того, линейчатые вложенно список уже в окно кода путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> метод.  Вызов <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> для  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> из  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Вызовите этот интерфейс, чтобы взаимодействовать непосредственно с вертикальной черты падающим вниз.  Этот интерфейс можно использовать для принудительного обновления содержимого раскрывающемся списке линейчатой диаграммы или изменить выделение в одном из списков.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Если зарегистрирован `ShowDropdownBarOption` в разделе реестра службы языка, затем в диспетчер окон кода должен контролировать это событие, чтобы синхронизировать с предпочтениями пользователя относительно, должно ли отображаться линии раскрывающемся списке.  Если не зарегистрировать этот параметр в своем ключе языковой службы, то параметр отображать или скрывать черта в раскрывающемся списке заблокирован **Параметры** меню.  
  
## Вложение черта раскрывающемся списке в окно кода  
 Чтобы вложить черта раскрывающемся списке в окне кода при его создании, служба языка должна вложить к гистограммам падающему когда вниз <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> вызывается метод.  Если вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>метод указывает, что полоса раскрывающемся списке еще не существует, то вызывается метод  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> .  Доступ <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> интерфейс, вызов  <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> от  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> указатель на возвращенный, когда  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> реализация была вложенна.  
  
## См. также  
 [Настройка кода Windows с помощью API прежних версий](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Поддержка панели навигации в языковую службу для прежних версий](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)