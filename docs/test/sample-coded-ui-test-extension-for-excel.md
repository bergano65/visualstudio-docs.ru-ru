---
title: Пример расширения закодированного теста пользовательского интерфейса для Excel | Документ Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 7c13ede1045734a1038cd89a8faab82c3b48f66d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Пример расширения закодированного теста пользовательского интерфейса для Excel
Компонент расширения примера выполняется в процессе закодированного теста пользовательского интерфейса [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и в некотором смысле является иерархическим с базовым классом `ExtensionPackage`. Классы `TechnologyManager`, `ActionFilter` и `PropertyProvider` находятся на следующем уровне, а элементы управления — на верхнем уровне.

 ![Архитектура расширения тестов в Excel](../test/media/excel_extarch.png "Excel_ExtArch") Архитектура расширения тестов в Excel

## <a name="extension-points"></a>Точки расширения
 Эти классы представляют точки расширения, реализованные в примере, чтобы сделать возможным применение к [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] закодированных тестов пользовательского интерфейса.

### <a name="extensionpackage"></a>ExtensionPackage
 Наследуется от класса <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>, является точкой входа для расширения закодированного теста пользовательского интерфейса. Реализация этого абстрактного класса предоставляет платформе закодированных тестов пользовательского интерфейса внутренний доступ к пользовательскому диспетчеру технологий тестирования пользовательского интерфейса, поставщику свойств тестирования пользовательского интерфейса и фильтру действий тестирования пользовательского интерфейса. Дополнительные сведения см. в разделе [Класс ExtensionPackage](../test/sample-excel-extension-extensionpackage-class.md).

### <a name="technologymanager"></a>TechnologyManager
 Наследуется от класса <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>, предоставляет диспетчер технологий для записи и воспроизведения тестов. Дополнительные сведения см. в разделе [Класс TechnologyManager](../test/sample-excel-extension-technologymanager-class.md).

### <a name="actionfilter"></a>ActionFilter
 Наследуется от класса <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> и предоставляет базовый класс для объединения результатов сходных действий теста в единый набор результатов теста. Дополнительные сведения см. в разделе [Класс ActionFilter](../test/sample-excel-extension-actionfilter-class.md).

### <a name="technology-elements"></a>Элементы технологии
 Базовый класс, наследуемый от <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>; реализует основу для элементов технологий в тестах пользовательского интерфейса, поддерживающих запись и воспроизведение. Дополнительные сведения см. в разделе [Классы Element](../test/sample-excel-extension-element-classes.md).

### <a name="propertyprovider"></a>PropertyProvider
 Наследуется от класса <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> и обеспечивает базовый класс для поддержки свойств элементов пользовательского интерфейса для записи и воспроизведения тестов. Дополнительные сведения см. в разделе [Класс PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md).

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Класс ExtensionPackage](../test/sample-excel-extension-extensionpackage-class.md)
- [Класс TechnologyManager](../test/sample-excel-extension-technologymanager-class.md)
- [Класс ActionFilter](../test/sample-excel-extension-actionfilter-class.md)
- [Классы Element](../test/sample-excel-extension-element-classes.md)
- [Класс PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md)
