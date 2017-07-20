---
title: "Пример расширения Excel. Класс ExtensionPackage | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 9
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 20e3ac96d5b12002b11a9e93b413c48738f57153
ms.contentlocale: ru-ru
ms.lasthandoff: 05/19/2017

---
# <a name="sample-excel-extension-extensionpackage-class"></a>Пример расширения Excel. Класс ExtensionPackage
Этот класс является расширением класса <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> и предоставляет точку входа для закодированного теста пользовательского интерфейса, используемого для тестирования листа [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
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

