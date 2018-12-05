---
title: Расширение закодированных тестов пользовательского интерфейса и записей действий
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: cbf4d89fc0a32501a2ea275c5168969dd2a0fd19
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894122"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Расширение закодированных тестов пользовательского интерфейса и записей действий

Платформа тестирования для закодированных пользовательских интерфейсов и записей действий поддерживает не все пользовательские интерфейсы. Возможно, пользовательский интерфейс, который вы хотите протестировать, не поддерживается. Например, невозможно напрямую создать закодированный тест пользовательского интерфейса или запись действия для электронной таблицы Microsoft Excel. Тем не менее можно создать собственное расширение для платформы закодированных тестов пользовательского интерфейса, которое будет поддерживать определенный пользовательский интерфейс, используя расширяемость такой платформы.

![Архитектура теста пользовательского интерфейса](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Пример расширения для тестирования Microsoft Excel

Эта [публикация блога](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/3-introducing-sample-excel-extension/) содержит ссылку на [пример расширения](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip) для платформы закодированных тестов пользовательского интерфейса. Вы также можете просмотреть всю [серию публикаций блога, посвященную расширяемости закодированных тестов пользовательского интерфейса](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/series-on-coded-ui-test-extensibility/).

> [!NOTE]
> Образец предназначен для использования с Microsoft Excel 2010. Он может поддерживать (или не поддерживать) другие версии Microsoft Excel.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Использование автоматизации пользовательского интерфейса для тестирования кода](../test/use-ui-automation-to-test-your-code.md)
- [Рекомендации по выполнению закодированных тестов пользовательского интерфейса](../test/best-practices-for-coded-ui-tests.md)
- [Поддерживаемые конфигурации и платформы для закодированных тестов пользовательского интерфейса и записей действий](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)