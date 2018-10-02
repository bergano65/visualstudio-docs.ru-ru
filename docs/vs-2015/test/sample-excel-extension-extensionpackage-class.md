---
title: Пример расширения Excel. Класс ExtensionPackage | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 11
ms.author: gewarren
manager: douge
ms.openlocfilehash: fadfbf9291daf35cea4e7ef3005cf3791c2fe052
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557905"
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Пример расширения Excel. Класс ExtensionPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [пример расширения Excel: класс ExtensionPackage](https://docs.microsoft.com/visualstudio/test/sample-excel-extension-extensionpackage-class).  
  
Этот класс является расширением класса <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> и предоставляет точку входа для закодированного теста пользовательского интерфейса, используемого для тестирования листа [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
## <a name="assembly-attribute"></a>Атрибут Assembly  
 Файл начинается с атрибута сборки, который определяет сборку как расширение теста пользовательского интерфейса.  
  
```  
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
    "ExcelExtensionPackage",  
    typeof(  
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]  
```  
  
 Этот атрибут объявляет имя базового класса, имя класса пакета и полное имя класса для пользовательского класса пакета расширения.  
  
## <a name="simple-properties"></a>Простые свойства  
 Этот класс содержит свойства, которые предоставляют значения, используемые платформой закодированных тестов пользовательского интерфейса для определения и описания расширения и сборки. Дополнительные сведения см. в комментариях, содержащихся в коде.  
  
## <a name="getservice-method"></a>Метод GetService  
 Метод <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> является единственной точкой входа, используемой платформой закодированных тестов пользовательского интерфейса для получения доступа к диспетчеру технологий, поставщику свойств и фильтру действий, которые определяются базовым классом для каждого объекта.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)



