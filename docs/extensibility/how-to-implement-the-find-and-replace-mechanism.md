---
title: "Практическое руководство: реализации поиска и замены механизм | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - поиск и замена"
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Практическое руководство: реализации поиска и замены механизм
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio предоставляет 2 способа реализации поиск\/заменяет.  Один из способов передачи образ текста в оболочке и препятствовал ей обрабатывать поиска, выбрав и замену текста.  Это позволяет пользователю указать несколько диапазонов текста.  Кроме того, в VSPackage может отслеживать этой функциональности.  В обоих случаях необходимо уведомить оболочка о текущем целевом объекте и целевых объектов для всех открытых документов.  
  
### Для реализации найти и заменить  
  
1.  Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> интерфейс на одном из объектов, возвращенных свойствами кадра  <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> OR  <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>.  Если создать специализированный редактор, необходимо реализовать этот интерфейс в виде части класса специализированного редактора.  
  
2.  Используйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> метод позволяет определить параметры, которые редактор поддерживает и отображения реализует ли поиск образа текста.  
  
     Если пользовательский редактор поддерживает образ текста при поиске реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     В противном случае \- средство <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>и  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> .  
  
3.  При реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> и  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> методы можно упростить, что при поиске задачи путем вызова  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> интерфейс.  
  
## См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>