---
title: "Практическое руководство: инициируют события, когда редактор фокус. | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - порождают события при потере фокуса"
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: инициируют события, когда редактор фокус.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Иногда необходимо знать, когда редактор теряет фокус на границе окна.  Например, можно извлечь код из окна кода после того, как редактор не будет сфокусирован на нем.  Следующая процедура описывает шаги для поиска получать уведомления фокуса редактора потери.  
  
### Создать событие в ответ на проигравшего фокус редактора  
  
1.  События элементов управления выделения, получая <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> объект  <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> и предоставление его в  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> объект.  
  
3.  В вызове функции <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>найдите  `elementid==SEID_WindowFrame`.  
  
4.  Проверьте `varValueNew` параметр 2 действий:  
  
    1.  Граница окна поиске.  
  
    2.  Точка, в которой программа теряет выделение в этой границе окна.