---
title: Начало разработки расширений Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 09/18/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 44403b5d60fc13666ffc6ec00558b80ef3a50ea9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144467"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Начало разработки расширений Visual Studio
Если не вы написали расширение Visual Studio, прежде чем, возможно, некоторые вопросы. Мы перечислены некоторые из наиболее распространенных здесь. Если вы не видите информацию вы ищете, используйте кнопки обратной связи (**Эта страница была полезной?** в нижней части экрана) попросить вас.  
  
## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Какое программное обеспечение нужно разрабатывать расширения Visual Studio?  
 Необходимо установить Visual Studio SDK в дополнение к Visual Studio для разработки расширений Visual Studio. Пакет SDK для Visual Studio можно установить в процессе обычной установки или его можно установить позже. Дополнительные сведения об установке пакета SDK для Visual Studio см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Какие элементы можно сделать с помощью расширений Visual Studio  
 Sky отрезка ограничение, когда дело доходит до представлять, различные расширения Visual Studio. Конечно большинство расширения имеют отношение к написанию кода, однако, не относится к. Ниже приведены некоторые примеры виды расширений, которые можно создать.  
  
-   Поддержка языков, которые не включены в Visual Studio с Цветовая подсветка синтаксиса, IntelliSense и поддержка компилятора и отладки  
  
-   Средства повышения производительности, которые расширяют ядро IDE опыт работы с дополнительные шаблоны, код рефакторинга, новые диалоговые окна и окна инструментов  
  
-   Конструкторы доменный сценариев, таких как поддержка конструктора или облачных данных  
  
 Примеры расширений извлечь [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Несколько модулей открытых источником и Marketplace содержит ссылки на их в репозитории GitHub. 
  
## <a name="which-visual-studio-features-can-i-extend"></a>Какие функции Visual Studio можно расширить  
 В теории, можно расширить практически любой частью Visual Studio: меню, панелей инструментов, команды, windows, решения, проекты, редакторы и т. д.  
  
 На практике найдено, используемых функций, большинство пользователей хотят расширить команд, меню и панелей инструментов, windows, IntelliSense и проекты. Ниже приведены ссылки на соответствующие разделы.  
  
-   [Расширение меню и команд](../extensibility/extending-menus-and-commands.md): добавить собственные элементы в меню Visual Studio и панели инструментов. Их можно использовать, чтобы запустить новые функциональные возможности Visual Studio или собственные внешние вспомогательные приложения. Можно также предоставить настраиваемые сочетания клавиш для элементов меню.  
  
-   [Расширение и настройка окна инструментов](../extensibility/extending-and-customizing-tool-windows.md): расширить существующий окна инструментов или создать собственные окна инструментов. Например, можно добавить новые свойства для **свойства**, или можно создать окно инструментов для добавления дополнительных функций.  
  
-   [Редактор и расширения службы языка](../extensibility/editor-and-language-service-extensions.md): добавлять свои собственные настройки IntelliSense для языков Visual Studio или создайте Поддержка новых языков программирования. Можно создать новое выполнение инструкций, предложения и новые подсказки кратких сведений. Лампочки можно добавить рефакторинга предложения и исправления кода для поддержки новых языков программирования.  
  
-   [Расширение проектов](../extensibility/extending-projects.md)  
  
-   [Расширение параметров и настроек пользователя](../extensibility/extending-user-settings-and-options.md)  
  
-   [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Изолированная оболочка Visual Studio](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a> Какие шаблоны проекта предоставляются VSSDK?  
 Два основных типа расширения, пакеты VSPackage и расширения MEF. В общем случае расширений VSPackage, используются для расширения, которые применяют или расширяют команд, окон инструментов и проекты. Расширений MEF позволяет расширить и настроить в редакторе Visual Studio.  
  
 Для расширений Visual C# и Visual Basic VSSDK предоставляет пустой шаблон проекта VSIX, который можно использовать вместе с шаблонами новых элементов, созданных команд меню, окна инструментов и расширений редактора. Можно также использовать этот шаблон, шаблоны проектов пакетов, фрагменты кода и других артефактов, для распространения среди других пользователей.  
  
 В C++ VSPackage мастер предоставляет код для добавления команд меню, окна инструментов и пользовательских редакторов.  
  
 Шаблон изолированной оболочки используется для расширения в оболочке Visual Studio, которую фирменной символики можно распространять в качестве собственного версии пакета. В следующих темах о начале работы с каждого типа расширения:  
  
-   Команды меню: [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   Окна инструментов: [создания расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   Расширения редактора: [создания расширения с помощью редактора шаблона элемента](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   Основные пакеты VSPackage: [создания расширения с помощью пакетов VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   Шаблон проекта VSIX: [Приступая к работе с использованием шаблона проекта VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Visual Studio isolated shell: [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Как получить расширение my должен выглядеть как Visual Studio?  
 Получить советы по проектированию пользовательского интерфейса для расширения в [Visual Studio техники](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="where-can-i-find-examples-of-vssdk-code"></a>Где можно найти примеры VSSDK кода  
 Каждый из перечисленных в предыдущем разделе ссылок имеют пошаговые руководства, которые демонстрируют реализации определенных функций. Можно также найти открытой примеры VSSDK на github на сайте [примеры Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  
  
## <a name="how-can-i-distribute-my-extension"></a>Как можно распределить расширение my  
 Можно установить расширение на другом компьютере или отправлять их в ваши друзья дает VSIX-файл, который можно установить, дважды щелкнув его. Можно найти дополнительные сведения о пакетах VSIX в [доставки расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Также можно опубликовать расширения в Visual Studio Marketplace, который сделает ее видимой в большое количество клиентов Visual Studio. Примером упаковка расширения в Marketplace. в разделе [Пошаговое руководство: публикация расширение Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Дополнительные сведения о том, что необходимо выполнить для публикации в Marketplace см. в разделе [продуктов и расширения для Visual Studio](/vsts/integrate/ide/extensions/overview).
