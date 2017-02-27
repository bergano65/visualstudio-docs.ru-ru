---
title: "Практическое руководство: размещения редактора в другом редакторе | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - размещения вложенного редактора"
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Практическое руководство: размещения редактора в другом редакторе
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В Visual Studio можно внутри другого редактора основного приложения путем указания размещения одного окна в качестве родительского окна.  Для этого задайте параметры <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> и  <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> во фрейме дочернего окна.  
  
### Настройка фрейм окна редактора к узлу  
  
1.  Обозначьте редактор, например в редакторе область окна размещенного путем создания дочернего окна.  
  
     Эта область, где будет направлена текстового редактора.  
  
2.  Создание редактора размещения использование <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> OR  <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод.  
  
3.  Установка <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> и  <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> свойства в реализации границы окна редактора сопоставленного с помощью передачи эти свойства в качестве параметров  <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> метод соответственно.  
  
     Если необходимо извлечь эти параметры, передайте эти свойства в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод.  
  
4.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> метод, содержащихся в редакторе.  
  
     Редактор отображается на панели размещенного, содержащий редактора.  
  
## Отказоустойчивость  
 **конструктор приложений** в Visual Studio Team Edition for architects примере границы окна редактора при размещении другой редактор.  **конструктор приложений** узлы других конструкторов в своей области справа.  Область конструктора \(или **Свойства** страница\) для каждого из конструкторов, которые содержат добавляется в фрейме окна.