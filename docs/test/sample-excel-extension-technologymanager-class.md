---
title: "Пример расширения Excel. Класс TechnologyManager | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# Пример расширения Excel. Класс TechnologyManager
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Этот класс расширяет класс <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> и отвечает за предоставление основных служб для расширения [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  Базовый класс содержит множество методов, однако в данном примере используется только их подмножество.  
  
 Некоторые методы лишь возвращают значение свойства.  Многие методы используются разработчиками для переопределения алгоритмов по умолчанию, встроенных в обработчик закодированных тестов пользовательского интерфейса.  Эти методы выдают исключение <xref:System.NotSupportedException> или возвращают значение `null`, в результате чего средой используется алгоритм по умолчанию.  
  
 В зависимости от сложности базовой технологии, разработка кода диспетчера технологий может занимать от нескольких недель до нескольких месяцев.  Excel предоставляет возможность создания диспетчера технологий, потенциально обладающего очень широкими функциональными возможностями.  Настоящий пример намеренно ограничен листами и ячейками Excel, и в нем используется лишь часть возможностей форматирования.  
  
 В коде диспетчера технологий по возможности используется канал удаленного взаимодействия .NET, открытый классом `Communicator` для извлечения данных из надстройки, выполняющейся в процессе Excel.  
  
## Видимость COM  
 Обратите внимание, что данный класс и все классы элементов, расширяющие класс <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>, содержат атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute> со значением `true` для обеспечения видимости этих классов для модели COM.  
  
## Свойство TechnologyName  
 Это переопределение свойства <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> должно предоставлять уникальное понятное имя, которое определяет базовую технологию для всех других компонентов расширения.  Для данного расширения используется значение "Excel".  
  
## Метод GetControlSupportLevel  
 Это переопределение метода <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> возвращает число, обозначающее уровень поддержки, который диспетчер технологий обеспечивает для элемента управления, представленного указанным дескриптором.  Чем выше возвращаемое значение, тем лучше диспетчер технологий поддерживает элемент управления.  В данном случае метод проверяет окно, содержащее элемент управления, и если оно является листом Excel, метод возвращает максимально возможное значение; в противном случае возвращается ноль, означающий, что поддержка не обеспечивается.  
  
## Методы получения элемента  
 Среда обработки закодированных тестов пользовательского интерфейса использует несколько важных методов для получения относящегося к технологии элемента путем указания дескриптора, точки на экране или элемента из другой технологии.  Код этих методов понятен без объяснений.  Базовые методы перечислены ниже.  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## Метод ParseQueryId  
 При создании закодированного теста пользовательского интерфейса можно указать значения свойств для некоторых или всех элементов управления в тесте.  Эти значения используются средой тестирования для создания пар "имя\-значение", которые называются свойствами поиска и используются для поиска определенных элементов управления пользовательского интерфейса в процессе выполнения теста.  Совокупность свойств поиска представляет значение свойства <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> каждого элемента технологии, которое включает каждый элемент управления.  Поскольку поиск элемента управления может выполняться несколько раз в течение теста, данный метод предоставляет диспетчеру технологий способ оптимизации синтаксического анализа свойств поиска для данного элемента управления.  Данный метод также возвращает файл Cookie, который может использоваться средой для последующих поисков элемента управления.  В этой реализации метода используется метод <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> для синтаксического анализа свойств поиска.  
  
## Метод MatchElement  
 Для выполнения поиска элементов управления диспетчером технологий можно реализовать метод <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> для возвращения массива возможных совпадений или вызова исключения <xref:System.NotSupportedException>, которое указывает среде использовать собственный алгоритм поиска.  В любом случае необходимо реализовать метод <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A>, и в этой реализации снова используется метод <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>.  
  
## Методы навигации  
 Эти методы получают родительские, дочерние или одноуровневые элементы для указанного элемента из иерархии пользовательского интерфейса.  Код является несложным и содержит понятные комментарии.  
  
## Внутренний метод GetExcelElement  
 Данный внутренний метод принимает дескриптор окна и сведения об элементе Excel и возвращает запрошенный элемент Excel.  
  
## См. также  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)