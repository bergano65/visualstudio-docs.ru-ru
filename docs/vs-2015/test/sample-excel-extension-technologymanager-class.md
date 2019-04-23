---
title: Пример расширения Excel. Класс TechnologyManager | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 11
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 64632c175b44a370d7dcaf48e7c0a8cee766a4ab
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078074"
---
# <a name="sample-excel-extension-technologymanager-class"></a>Пример расширения Excel. Класс TechnologyManager
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Этот класс расширяет класс <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> и отвечает за предоставление основных служб для расширения [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]. Базовый класс содержит множество методов, однако в этом примере используется только их подмножество.  
  
 Некоторые методы лишь возвращают значение свойства. Многие методы используются разработчиками для переопределения алгоритмов по умолчанию, встроенных в модуль закодированных тестов пользовательского интерфейса. Эти методы выдают исключение <xref:System.NotSupportedException> или возвращают значение `null`, в результате чего средой используется алгоритм по умолчанию.  
  
 В зависимости от сложности базовой технологии разработка кода диспетчера технологий может занимать от нескольких недель до нескольких месяцев. Excel предоставляет возможность создания диспетчера технологий, потенциально обладающего очень широкими функциональными возможностями. Данный пример намеренно ограничен листами и ячейками Excel, и в нем используется лишь часть возможностей форматирования.  
  
 В коде диспетчера технологий по возможности используется канал удаленного взаимодействия .NET, открытый классом `Communicator` для извлечения данных из надстройки, выполняющейся в процессе Excel.  
  
## <a name="com-visibility"></a>Видимость COM  
 Обратите внимание, что данный класс и все классы элементов, расширяющие класс <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>, содержат атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute> со значением `true` для обеспечения видимости этих классов для модели COM.  
  
## <a name="technologyname-property"></a>Свойство TechnologyName  
 Это переопределение свойства <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> должно предоставлять уникальное понятное имя, которое определяет базовую технологию для всех других компонентов расширения. Для данного расширения используется значение "Excel".  
  
## <a name="getcontrolsupportlevel-method"></a>Метод GetControlSupportLevel  
 Это переопределение метода <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> возвращает число, обозначающее уровень поддержки, который диспетчер технологий обеспечивает для элемента управления, представленного указанным дескриптором. Чем выше возвращаемое значение, тем лучше диспетчер технологий поддерживает элемент управления. В данном случае метод проверяет окно, содержащее элемент управления, и если оно является листом Excel, метод возвращает максимально возможное значение. В противном случае возвращается ноль, означающий, что поддержка не обеспечивается.  
  
## <a name="methods-to-get-an-element"></a>Методы получения элемента  
 Платформа закодированных тестов пользовательского интерфейса использует несколько важных методов для получения относящегося к технологии элемента путем указания дескриптора, точки на экране или элемента из другой технологии. Код этих методов понятен без объяснений. Базовые методы перечислены ниже.  
  
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## <a name="parsequeryid-method"></a>Метод ParseQueryId  
 При создании закодированного теста пользовательского интерфейса можно указать значения свойств для некоторых или всех элементов управления в тесте. Эти значения используются средой тестирования для создания пар "имя-значение", которые называются свойствами поиска и применяются для поиска определенных элементов управления пользовательского интерфейса в процессе выполнения теста. Это переопределение метода <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> возвращает число, обозначающее уровень поддержки, который диспетчер технологий обеспечивает для элемента управления, представленного указанным дескриптором. Так как поиск элемента управления может выполняться несколько раз в течение теста, этот метод предоставляет диспетчеру технологий способ оптимизации синтаксического анализа свойств поиска для данного элемента управления. Этот метод также возвращает файл cookie, который может использоваться платформой для последующих поисков элемента управления. В этой реализации метода для синтаксического анализа свойств поиска используется метод <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>.  
  
## <a name="matchelement-method"></a>Метод MatchElement  
 Для выполнения поиска элементов управления вы можете реализовать метод <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> или для возвращения массива возможных совпадений или вызова исключения — метод <xref:System.NotSupportedException>, который указывает среде использовать собственный алгоритм поиска. В любом случае необходимо реализовать метод <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A>, и в этой реализации снова используется метод <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>.  
  
## <a name="navigation-methods"></a>Методы навигации  
 Эти методы получают родительские, дочерние или одноуровневые элементы для указанного элемента из иерархии пользовательского интерфейса. Код несложен и содержит понятные комментарии.  
  
## <a name="getexcelelement-internal-method"></a>Внутренний метод GetExcelElement  
 Этот внутренний метод принимает дескриптор окна и сведения об элементе Excel и возвращает запрошенный элемент Excel.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
