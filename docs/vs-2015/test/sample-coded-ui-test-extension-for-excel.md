---
title: Пример расширения закодированного теста пользовательского интерфейса для Excel | Документ Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: 15
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e0c6075f9f95f7dc1d21db91936cf35c76f9b2e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672233"
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Пример расширения закодированного теста пользовательского интерфейса для Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Компонент расширения примера выполняется в процессе закодированного теста пользовательского интерфейса [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и в некотором смысле является иерархическим с базовым классом `ExtensionPackage`. Классы `TechnologyManager`, `ActionFilter` и `PropertyProvider` находятся на следующем уровне, а элементы управления — на верхнем уровне.

 ![Архитектура расширения теста Excel](../test/media/excel-extarch.png "Excel_ExtArch") Архитектура расширения Excel

## <a name="extension-points"></a>Точки расширения
 Эти классы представляют точки расширения, реализованные в примере, чтобы сделать возможным применение к [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] закодированных тестов пользовательского интерфейса.

### <a name="extensionpackage"></a>ExtensionPackage
 Наследуется от класса <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>, является точкой входа для расширения закодированного теста пользовательского интерфейса. Реализация этого абстрактного класса предоставляет платформе закодированных тестов пользовательского интерфейса внутренний доступ к пользовательскому диспетчеру технологий тестирования пользовательского интерфейса, поставщику свойств тестирования пользовательского интерфейса и фильтру действий тестирования пользовательского интерфейса. Дополнительные сведения см. в разделе [Класс ExtensionPackage](../test/sample-excel-extension-extensionpackage-class.md).

### <a name="technologymanager"></a>TechnologyManager
 Наследуется от класса <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>, предоставляет диспетчер технологий для записи и воспроизведения тестов. Дополнительные сведения см. в разделе [Класс TechnologyManager](../test/sample-excel-extension-technologymanager-class.md).

### <a name="actionfilter"></a>ActionFilter
 Этот класс, унаследованный от класса [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) , предоставляет базовый класс для статистической обработки аналогичных результатов действий теста в одном результате теста. Дополнительные сведения см. в разделе [Класс ActionFilter](../test/sample-excel-extension-actionfilter-class.md).

### <a name="technology-elements"></a>Элементы технологии
 Базовый класс, наследуемый от <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>; реализует основу для элементов технологий в тестах пользовательского интерфейса, поддерживающих запись и воспроизведение. Дополнительные сведения см. в разделе [Классы Element](../test/sample-excel-extension-element-classes.md).

### <a name="propertyprovider"></a>PropertyProvider
 Наследуется от класса <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> и обеспечивает базовый класс для поддержки свойств элементов пользовательского интерфейса для записи и воспроизведения тестов. Дополнительные сведения см. в разделе [Класс PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md).

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Класс ExtensionPackage](../test/sample-excel-extension-extensionpackage-class.md)
- [Класс TechnologyManager](../test/sample-excel-extension-technologymanager-class.md)
- [Класс ActionFilter](../test/sample-excel-extension-actionfilter-class.md)
- [Классы Element](../test/sample-excel-extension-element-classes.md)
- [Класс PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md)
