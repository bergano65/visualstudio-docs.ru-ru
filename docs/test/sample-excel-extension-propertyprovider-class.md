---
title: "Пример расширения Excel. Класс PropertyProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# Пример расширения Excel. Класс PropertyProvider
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Этот внутренний класс расширяет класс <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> и обеспечивает свойства для элементов [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)], чтобы можно было записывать и воспроизводить тесты пользовательского интерфейса.  
  
## Метод GetControlSupportLevel  
 Метод <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> возвращает число, обозначающее уровень поддержки, обеспечиваемый поставщиком свойства для указанного элемента управления.  Чем выше это значение, тем лучше поставщик свойства поддерживает элемент управления.  В данном случае метод проверяет значение свойства <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> указанного элемента управления.  Если значение равняется Excel, а свойство <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> задает `CellElement`, метод возвращает наибольшее значение; в противном случае он возвращает ноль, что означает, что поддержка не предоставляется.  
  
## Метод GetPropertyNames  
 Возвращает словарь имен и дескрипторов свойств для поддерживаемых свойств элемента управления Excel Cell.  
  
## Метод GetPropertyDescriptor  
 Этот метод вызывается тестовой средой для получения предварительно определенного дескриптора свойства для указанного имени свойства.  
  
## Методы GetPropertyValue и SetPropertyValue  
 Метод `GetPropertyValue` использует класс `Communicator` этого расширения, чтобы возвращать значение свойства из Excel.  Метод `SetPropertyValue` использует класс <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> и компонент `Communicator`, чтобы задавать значение свойства.  Эти методы вызываются средой тестирования.  
  
## Методы настройки создания кода  
 Для данного расширения эти методы не реализованы.  Поэтому они возвращают значение `null` или вызывают исключение <xref:System.NotImplementedException>.  
  
## См. также  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>   
 [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)