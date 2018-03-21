---
title: "Пример расширения Excel. Класс ExtensionPackage | Документы Майкрософт"
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2d4c7b5c3aefbc59b8e8931376f0bcf14951c9bc
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
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

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
