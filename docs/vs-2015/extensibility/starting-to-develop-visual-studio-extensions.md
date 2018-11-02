---
title: Приступая к разработке расширений Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3a38410c1b64a455f12d91cd8460f5f04d369275
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847309"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Приступая к разработке расширений Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если вы не написали ни расширение Visual Studio, прежде чем, возможно, некоторые вопросы. Мы перечислили некоторые из самых распространенных рисков здесь. Если вы не видите сведения, которые вы ищете, используйте кнопки обратной связи (**Эта страница была полезной?** в нижней части экрана) за то, что нужно.  
  
## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Какое программное обеспечение требуется для разработки расширений Visual Studio?  
 Необходимо установить SDK для Visual Studio 2015 в дополнение к Visual Studio 2015 для разработки расширений Visual Studio.   SDK для Visual Studio 2015 можно установить как часть обычной установки или его можно установить позже. Дополнительные сведения об установке Visual Studio SDK, см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Какие элементы можно сделать с помощью расширений Visual Studio?  
 Передохнуть когда дело доходит до описывая различные расширения Visual Studio. Само собой большинство расширений имеет какое-то написанию кода, но, не обязательно так. Ниже приведены некоторые примеры различных типов расширений, которые можно создавать.  
  
- Поддержка языков, которые не включены в Visual Studio с синтаксических конструкций, IntelliSense и поддержку компилятора и отладки  
  
- Средства повышения производительности, расширить интегрированную среду разработки опыт дополнительные шаблоны, рефакторинга, новые диалоговые окна кода или окна инструментов  
  
- Конструкторы предметно ориентированных сценариев, таких как поддержка разработки или облачных данных  
  
  Примеры расширения, ознакомьтесь с [коллекции Visual Studio](https://visualstudiogallery.msdn.microsoft.com/). Вы также можете рассмотреть [откройте Visual Studio, расширения источников](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md).  
  
## <a name="which-visual-studio-features-can-i-extend"></a>Какие возможности Visual Studio можно расширить?  
 В теории, вы можете расширить практически любую часть Visual Studio: меню, панелей инструментов, команды, windows, решения, проекты, редакторы и т. д.  
  
 На практике мы обнаружили, что большинство людей, необходимые для расширения функции являются команды, меню и панелей инструментов, windows, IntelliSense и проекты. Ниже приведены ссылки на соответствующие разделы.  
  
-   [Расширение меню и команд](../extensibility/extending-menus-and-commands.md): добавлять собственные элементы в меню Visual Studio и на панели инструментов. Их можно использовать для запуска новых функций Visual Studio или собственные внешние вспомогательные приложения. Можно также предоставить настраиваемые сочетания клавиш для элементов меню.  
  
-   [Расширение и настройка Windows средство](../extensibility/extending-and-customizing-tool-windows.md): расширения существующих окон инструментов или создавать собственные окна инструментов. Например, можно добавить новые свойства для **свойства**, или можно создать новое окно инструментов для добавления дополнительных функций.  
  
-   [Редактор и расширения службы языка](../extensibility/editor-and-language-service-extensions.md): Добавление собственных настроек данные IntelliSense для языков Visual Studio, или создайте Поддержка новых языков программирования. Можно создать новый завершение инструкций, предложения и новые отображение подсказок. Лампочки вы можете добавить рефакторинга предложения и средства исправления кода для поддержки новых языков программирования.  
  
-   [Расширение проектов](../extensibility/extending-projects.md)  
  
-   [Расширение параметров и настроек пользователя](../extensibility/extending-user-settings-and-options.md)  
  
-   [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Изолированная оболочка Visual Studio](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a> Какие шаблоны проектов, предоставляемые VSSDK?  
 Два основных типа расширения являются пакеты VSPackage и расширения MEF. В общем случае расширений VSPackage используются для расширения, которые применяют или расширяют команд, окон инструментов и проекты. Расширения MEF позволяют расширить и настроить в редакторе Visual Studio.  
  
 Для расширения Visual C# и Visual Basic VSSDK предоставляет пустой шаблон проекта VSIX, который можно использовать вместе с шаблонами новых элементов, которые создают команды меню, окна инструментов и расширения редактора. Дополнительные сведения см. в разделе [новые возможности пакета SDK для Visual Studio 2015](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md). Этот шаблон, шаблоны проектов пакетов, фрагменты кода и другие артефакты можно также использовать для распространения другим пользователям.  
  
 Для C++ мастер VSPackage предоставляет код для добавления команды меню, окна инструментов и специальные редакторы.  
  
 Шаблон изолированной оболочки используется для упаковки расширения в версиях, которую можно Добавление фирменной символики и распространять как собственные оболочки Visual Studio. Следующие разделы показывают, как приступить к работе с каждого вида расширения:  
  
-   Команды меню: [создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   Окна инструментов: [создание расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   Расширения редактора: [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   Основные пакеты VSPackage: [Creating an Extension with VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   Шаблон проекта VSIX: [Приступая к работе с шаблоном проекта VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Изолированная оболочка Visual Studio: [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Как получить расширение my, чтобы он выглядел Visual Studio?  
 Полезные советы по проектированию пользовательского интерфейса для расширения в [по работе пользователей Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="where-can-i-find-examples-of-vssdk-code"></a>Где найти примеры VSSDK кода?  
 Каждый из ссылок, перечисленных в предыдущем разделе иметь пошаговые руководства, которые показано, как реализовать определенные функции. Можно также найти открытым исходным кодом примеры VSSDK на сайте GitHub в [примеры Visual Studio](https://aka.ms/vs2015sdksamples).  
  
## <a name="how-can-i-distribute-my-extension"></a>Как можно распространять Мои расширения?  
 Можно установить расширение на другом компьютере или отправить его своим друзьям как VSIX-файл, который можно установить, дважды щелкнув его. Можно найти дополнительные сведения о пакетах VSIX в [доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Также можно опубликовать ваше расширение в коллекции Visual Studio, что делает его видимым на большом числе клиентов Visual Studio. Пример того, упаковка расширения для коллекции, см. в разделе [Пошаговое руководство: публикация расширения Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Дополнительные сведения о что необходимо сделать, чтобы опубликовать в коллекции, см. в разделе [продукты и расширения для Visual Studio](https://visualstudiogallery.msdn.microsoft.com/).

