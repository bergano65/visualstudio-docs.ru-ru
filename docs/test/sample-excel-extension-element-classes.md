---
title: "Пример расширения Excel. Классы Element | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "mlearned"
manager: "douge"
---
# Пример расширения Excel. Классы Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Расширение использует классы, которые являются производными от класса <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> и представляют элементы управления "Лист" и "Ячейка" в приложении [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
 Базовым элементом для данного расширения является `ExcelElement`.  От этого элемента наследуют классы `ExcelWorksheetElement` и `ExcelCellElement`.  
  
## Классы Element и ElementInformation  
 `Element`  является базовым классом для всех элементов пользовательского интерфейса для расширения Excel; он является производным от класса <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>.  `ElementInformation` является базовым классом для классов информации об элементах в примере; он не содержит членов.  
  
#### Простые свойства и методы  
 Эти члены возвращают простые значения, например значение свойства `Name` или `ClassName`; код этих членов является простым и удобным для чтения.  Некоторые значения возвращаются с помощью класса `Utility`, который рассматривается ниже.  Прочие члены возвращают значение `null`, поскольку они не имеют отношения к данному примеру расширения.  Два члена имеют большее значение по сравнению с остальными: свойство <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> и метод <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A>.  
  
#### Свойство QueryId  
 Это свойство возвращает условие, составленное из пары "имя\-значение свойства", которое уникальным образом определяет элемент управления во время воспроизведения.  Разработчик должен переопределить это свойство в каждом производном классе элемента управления, чтобы возвратить объект <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>, который может использоваться средой для поиска элемента управления в пользовательском интерфейсе.  
  
#### Метод CacheProperties  
 Этот метод вызывается средой тестирования во время процесса записи, чтобы указать элементу сохранить снимок важных свойств.  Благодаря этому свойства остаются доступными, даже если фактический элемент управления пользовательского интерфейса больше не отображается на экране.  
  
## Классы WorksheetElement и WorksheetInformation  
 Класс `WorksheetElement` представляет лист Excel в среде тестирования; он наследуют от базового класса `Element`.  Для предоставления конкретной информации об объекте листа Excel переопределяются три свойства: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A> и <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>.  
  
 К этому классу также применяется атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute>, чтобы сделать класс видимым для модели COM.  
  
 Класс `WorksheetInformation` представляет информацию о листе Excel.  У него имеется только один член — свойство `SheetName`, однако этого достаточно для целей примера.  
  
## Классы CellElement и CellInformation  
 Класс `CellElement` представляет ячейку Excel; он наследует от базового класса `Element`.  Его единственным переопределенным членом является свойство <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>, которое возвращает объект <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>, использующий свойства `RowIndex` и `ColumnIndex` для определения ячейки.  
  
## Классы Utilities и ExcelUtilities  
 Внутренний класс `ExcelUtilities` предоставляет некоторые константные значения, такие как имя технологии, а также метод, который определяет, действительно ли указанный дескриптор окна представляет лист Excel.  
  
 Класс `Utilities` содержит вспомогательные методы, которые возвращают самые различные сведения о пользовательском интерфейсе.  Некоторые методы используют прямые вызовы внешних системных библиотек DLL, таких как **USER32.DLL** и **OLEACC.DLL**, для получения дескрипторов окна из пользовательского интерфейса**.**  
  
## См. также  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>   
 [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)