---
title: "Пример расширения Excel. Класс ExtensionPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# Пример расширения Excel. Класс ExtensionPackage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Этот класс расширяет класс <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> и предоставляет точку входа для закодированного теста пользовательского интерфейса, используемого для тестирования листа [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
## Атрибут Assembly  
 Файл начинается с атрибута сборки, который определяет сборку как расширение теста пользовательского интерфейса.  
  
```  
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
    "ExcelExtensionPackage",  
    typeof(  
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]  
```  
  
 Этот атрибут объявляет имя базового класса, имя класса пакета и полное имя класса для пользовательского класса пакета расширения.  
  
## Простые свойства  
 Этот класс содержит свойства, которые предоставляют значения, используемые средой обработки закодированных тестов пользовательского интерфейса для определения и описания расширения и сборки.  Дополнительные сведения см. в комментариях, содержащихся в коде.  
  
## Метод GetService  
 Метод <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> является единственной точкой входа, используемой средой обработки закодированных тестов пользовательского интерфейса для получения доступа к диспетчеру технологий, поставщику свойств и фильтру действий, которые определяются базовым классом для каждого объекта.  
  
## См. также  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)