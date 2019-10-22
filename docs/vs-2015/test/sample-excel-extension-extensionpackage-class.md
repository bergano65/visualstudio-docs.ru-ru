---
title: Пример расширения Excel. Класс ExtensionPackage | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1c1f4c746fa505b50bab9caa7a516a2abc77f69
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672208"
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Пример расширения Excel. Класс ExtensionPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="see-also"></a>См. также раздел
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
