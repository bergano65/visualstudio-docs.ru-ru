---
title: Начиная с разработки визуальных расширений студии (ru) Документы Майкрософт
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 744475e61458f7b91ce08fba4d17046df36f5558
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699737"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Приступая к разработке расширений Visual Studio

Если вы никогда не писали расширение Visual Studio раньше, у вас, вероятно, есть некоторые вопросы. Мы перечислили некоторые из наиболее распространенных из них здесь. Если вы не видите информацию, которая вы ищете, используйте кнопки обратной связи **(Была ли эта страница полезно?** в нижней части экрана), чтобы спросить, что вы хотите.

> [!NOTE]
> Эта статья относится к Visual Studio на Windows. Для визуальной студии для Mac, см [Расширение Visual Studio для Mac](/visualstudio/mac/extending-visual-studio-mac). Для Визуального кода [Visual Studio Code Extension API](https://code.visualstudio.com/api)студии см.

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Какое программное обеспечение мне нужно для разработки расширений Visual Studio?

Вам нужно установить Visual Studio SDK в дополнение к Visual Studio для того, чтобы развивать визуальные расширения studio. Вы можете установить Visual Studio SDK как часть регулярной настройки, или вы можете установить его позже. Для получения дополнительной информации об установке Визуальной студии SDK, [см.](../extensibility/visual-studio-sdk.md)

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Какие действия я могу сделать с расширениями Visual Studio?

Небо предел, когда дело доходит до воображая различные визуальные расширения studio. Конечно, большинство расширений имеют какое-то отношение к написанию кода, но это не должно быть так. Вот несколько примеров видов расширений, которые можно построить:

- Поддержка языков, не включенных в Visual Studio, с окраской синтаксиса, IntelliSense, а также поддержкой компилятора и отладки

- Инструменты производительности, расширяющие основной опыт IDE с дополнительными шаблонами, рефакторингом кода, новыми диалогами или окнами инструментов

- Дизайнеры для конкретных доменов для таких сценариев, как проектирование данных или поддержка облаков

Для примеров расширений, проверить [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Многие расширения с открытым исходным кодом, и Marketplace включает в себя ссылки на их Репо GitHub.

## <a name="which-visual-studio-features-can-i-extend"></a>Какие функции Visual Studio я могу расширить?

Теоретически, вы можете расширить почти любую часть Visual Studio: меню, панели инструментов, команды, окна, решения, проекты, редакторы и так далее.

На практике мы обнаружили, что функции, которые большинство людей хотят расширить, это команды, меню и панели инструментов, окна, IntelliSense и проекты. Вот ссылки на соответствующие разделы:

- [Расширение меню и команд](../extensibility/extending-menus-and-commands.md): добавляйте свои собственные элементы в меню Visual Studio и панели инструментов. Вы можете использовать их для запуска новой функциональности Visual Studio или ваших собственных внешних приложений помощника. Вы также можете предоставить пользовательские ярлыки для элементов меню.

- [Расширение и настройка инструмента Windows:](../extensibility/extending-and-customizing-tool-windows.md)расширение существующих окон инструментов или создание собственных окон инструментов. Например, можно добавить новые свойства в **свойства,** или создать новое окно инструмента для добавления дополнительных функций.

- [Расширения отдела редактора и языковой службы](../extensibility/editor-and-language-service-extensions.md): добавляйте свои собственные настройки в IntelliSense, предусмотренные для языков Visual Studio, или создавайте поддержку новых языков программирования. Можно создать новые завершения, предложения и новые наборы инструментов для быстрого инфоди. С помощью лампочек можно добавлять предложения рефакторинга и исправления кода для поддержки новых языков программирования.

- [Расширение проектов](../extensibility/extending-projects.md)

- [Расширение параметров и настроек пользователя](../extensibility/extending-user-settings-and-options.md)

- [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md)

- [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Изолированная оболочка Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a>Какие шаблоны проекта предоставляются VSSDK?
 Двумя основными типами расширений являются VSPackages и расширения MEF. В целом расширения VSPackage используются для расширений, которые используют или расширяют команды, окна инструментов и проекты. Расширения MEF используются для расширения или настройки редактора Visual Studio.

 Для визуальных и визуальных базовых расширений VSSDK предоставляет пустой шаблон проекта VSIX, который можно использовать вместе с новыми шаблонами элементов, которые создают команды меню, окна инструментов и расширения редактора. Вы также можете использовать этот шаблон для упаковки шаблонов проектов, фрагментов кода и других артефактов для распространения среди других пользователей.

 Для СЗ мастер VSPackage предоставляет код для добавления команд меню, окон инструментов и пользовательских редакторов.

 Шаблон Изолированной оболочки используется для упаковки расширения в версии оболочки Visual Studio, которую можно заклеймить и распространять как свою собственную. Следующие темы показывают, как начать работу с каждым видом расширения:

- Команды меню: [Создание расширения с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md)

- Окна [инструментов: Создание расширения с окном инструмента](../extensibility/creating-an-extension-with-a-tool-window.md)

- Расширение редактора: [Создание расширения с шаблоном элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Основные VSPackages: [Создание расширения с VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- Шаблон проекта VSIX: [Начало работы с шаблоном проекта VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Как получить, чтобы расширение выглядело как Visual Studio?
 Получите отличные советы по разработке пользовательского интерфейса для вашего расширения в [Visual Studio Пользовательские Рекомендации по опыту.](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Где я могу найти примеры кода VSSDK?
 Каждая из ссылок, перечисленных в предыдущем разделе, имеет пошаговые пошаговые пошаговые пошаговые пошаговые пошаговые проекты, которые показывают, как реализовать определенные функции. Вы также можете найти с открытым исходным кодом VSSDK образцы на GitHub в [Visual Studio Образцы](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>Как я могу распространить расширение?
 Вы можете установить расширение на другом компьютере или отправить его своим друзьям в качестве файла .vsix, который вы устанавливаете, дважды нажав на него. Вы можете узнать больше о пакетах VSIX в [Shipping Visual Studio Extensions.](../extensibility/shipping-visual-studio-extensions.md)

 Вы также можете опубликовать свое расширение на Visual Studio Marketplace, что делает его видимым для большого числа клиентов Visual Studio. Для примера упаковки расширения на Marketplace [см.](../extensibility/walkthrough-publishing-a-visual-studio-extension.md) Для получения дополнительной информации о том, что вам нужно сделать, чтобы опубликовать на Marketplace, [см.](/azure/devops/extend/overview?view=vsts)

## <a name="see-also"></a>См. также

- [Расширение Visual Studio для Mac](/visualstudio/mac/extending-visual-studio-mac)
- [Расширение кода визуальной студии](https://code.visualstudio.com/api)
