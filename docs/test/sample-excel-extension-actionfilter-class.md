---
title: "Пример расширения Excel. Класс ActionFilter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 11
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 11
---
# Пример расширения Excel. Класс ActionFilter
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Этот внутренний класс расширяет класс <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> и представляет фильтр для действий теста по отношению к элементу [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
## Простые свойства  
 Эти свойства только для чтения позволяют разработчику указывать способ выполнения фильтра действий теста средой обработки закодированных тестов пользовательского интерфейса.  Например, свойство <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> предоставляет имя фильтра действий.  Другие свойства получают категорию \(<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>\) фильтра действий, тип фильтра \(<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>\), имя группы \(<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A>\) для действий теста, фильтруемых данным фильтром действий.  Другие свойства определяют, следует ли применять время ожидания \(<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>\), а также включен ли фильтр действий теста \(<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>\).  
  
## Метод ProcessRule  
 Этот метод вызывается средой обработки закодированных тестов пользовательского интерфейса; он выполняет фильтр для предоставленного объекта <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>.  Данное переопределение удаляет действие щелчка мыши в ячейке, если следующее действие в стеке отправляет нажатия клавиш клавиатуры в этой ячейке.  Затем оно возвращает значение `false`.  
  
## Частные методы  
 Метод `IsLeftClick` определяет, представляет ли указанное действие щелчок левой кнопкой мыши.  Метод `AreActionsOnSameExcelCell` определяет, выполняются ли два указанных действия в одной ячейке Excel.  
  
## См. также  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)