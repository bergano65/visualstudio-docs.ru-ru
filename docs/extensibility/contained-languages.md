---
title: "Автономные языков | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - автономной языков"
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Автономные языков
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Содержит языки* языки, в которых содержатся другие языки.  Например, в HTML [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] страницы могут содержаться  [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] OR  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] скрипты.  Требуется для редактора файла .aspx предоставляет архитектура двойн\-языка IntelliSense, колоризацию и другие функции, такие как для редактирования HTML, так и для языка скриптов.  
  
## Реализация  
 Самый важный интерфейс необходимо реализовывать для включенных языков <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> интерфейс.  Этот интерфейс реализован любым языком, который может быть размещен внутри основного языка.  Он предоставляет доступ к colorizer языковой службы, фильтру представления текста и идентификатору службы основной язык  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> позволяет создать  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> интерфейс.  Следующие шаги демонстрируют способы реализации, которые содержат язык:  
  
1.  Используйте `QueryService()` получить идентификатор языковой службы и идентификатор интерфейса  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> метод создания  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> интерфейс.  Передайте <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейс идентификатор элемента \(один или несколько  <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>"  <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>или  <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>\) и  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> интерфейс.  
  
3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> интерфейс, который является объектом координатора текстового буфера предоставляет основные службы, которые требуется сопоставить расположения в первичном файле в буфер вторичного языка.  
  
     Например, в одном aspx\-файле, первичный файл содержит ASP, HTML и весь код, содержащийся.  Однако вторичный буфер, содержит только код, содержащийся вместе с всеми определениями класса, чтобы сделать вторичным буфером допустимый файл кода.  Координатор буфера обрабатывает рабочего буфера координирующая правок из одного в другой.  
  
4.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> метод, который основного языка\) сообщает, какие координатору буфера текст в свой буфер сопоставлено с соответствующим текст в поле вторичный буфер.  
  
     Язык передает в массив <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> структура, которая в настоящее время содержит только первичный и вторичный диапазон.  
  
5.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> метод и  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> метод обеспечивает сопоставление из первичного вторичный буфер и наоборот.