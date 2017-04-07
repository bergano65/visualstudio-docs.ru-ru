---
title: "Начиная разрабатывать расширения Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: dc5416fe979ed3e52ef2df77e5b495cb98038dcd
ms.lasthandoff: 03/07/2017

---
# <a name="starting-to-develop-visual-studio-extensions"></a>Начиная разрабатывать расширения Visual Studio
Если вам не доводилось писать расширение Visual Studio, прежде чем, возможно, некоторые вопросы. Мы перечислены некоторые наиболее распространенные здесь. Если вы не видите вы ищете информацию, используйте кнопки обратной связи (**была Эта страница полезной?** в нижней части экрана) попросить вас.  
  
## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Какое программное обеспечение необходимо для разработки расширений Visual Studio  
 Необходимо установить Visual Studio SDK, в дополнение к Visual Studio для разработки расширений Visual Studio. Visual Studio SDK можно установить как часть обычной установки, или можно установить позже. Дополнительные сведения об установке пакета SDK для Visual Studio см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Какие элементы можно сделать с помощью расширений Visual Studio  
 Возможности безграничны когда дело доходит до представляете различных расширений Visual Studio. Конечно большинство расширений было что-то делать с написания кода, но, не обязательно так. Ниже приведены некоторые примеры типов расширения, которые можно создавать:  
  
-   Поддержка языков, не включенные в Visual Studio с Цветовая подсветка синтаксиса, IntelliSense и поддержки компилятора и отладки  
  
-   Средства повышения производительности, расширить IDE опыт дополнительные шаблоны, код рефакторинга, новые диалоговые окна и окна инструментов  
  
-   Доменный конструкторы для таких сценариев, как поддержка разработки и облако данных  
  
 Примеры расширения, ознакомьтесь с [коллекции Visual Studio](https://visualstudiogallery.msdn.microsoft.com/). Вы также можете рассмотреть [откройте источник оснастки расширения Visual Studio](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md).  
  
## <a name="which-visual-studio-features-can-i-extend"></a>Какие функции Visual Studio можно расширить  
 В теории, можно расширить практически любую часть Visual Studio: меню, панелей инструментов, команды, windows, решения, проекты, редакторы и т. д.  
  
 На практике мы нашли, большинство людей необходимо расширить функции команд, меню и панелей инструментов, windows, IntelliSense и проекты. Ниже приведены ссылки на соответствующие разделы.  
  
-   [Расширение меню и команд](../extensibility/extending-menus-and-commands.md): добавлять собственные элементы в меню Visual Studio и на панели инструментов. Их можно использовать для запуска новых функций Visual Studio или вспомогательный внешних приложений. Можно также предоставить пользовательские ярлыки для элементов меню.  
  
-   [Расширение и настройка Windows средство](../extensibility/extending-and-customizing-tool-windows.md): расширить существующие средства windows или создать собственные окна инструментов. Например, можно добавить новые свойства в **свойства**, или можно создать новое окно инструмента для добавления дополнительных функций.  
  
-   [Редактор и расширения языка службы](../extensibility/editor-and-language-service-extensions.md): Добавление собственных настроек IntelliSense для языков Visual Studio или создайте Поддержка новых языков программирования. Можно создать новый выполнение инструкций, предложений и новые подсказки кратких сведений. Лампочки можно добавить предложения рефакторинга и исправления кода для поддержки новых языков программирования.  
  
-   [Расширение проектов](../extensibility/extending-projects.md)  
  
-   [Расширение параметров и настроек пользователя](../extensibility/extending-user-settings-and-options.md)  
  
-   [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Изолированная оболочка Visual Studio](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a>Какие шаблоны проектов, предоставляемые VSSDK?  
 Два основных типа расширения являются расширениями VSPackages и MEF. Как правило расширения VSPackage используются для расширения, которые применяют или расширяют команд, окон инструментов и проекты. MEF расширения используются для расширения и настройки в редакторе Visual Studio.  
  
 Для расширения Visual C# и Visual Basic VSSDK предоставляет пустой шаблон проекта VSIX, который можно использовать вместе с шаблонами новых элементов, создание команды меню, окна инструментов и расширения редактора. Можно также использовать этот шаблон для пакета шаблонов проектов, фрагменты кода и других артефактов, для распространения среди других пользователей.  
  
 В C++ VSPackage мастер предоставляет код для добавления команды меню, окна инструментов и специальные редакторы.  
  
 Шаблон изолированной оболочки используется для упаковки расширения в версии оболочки Visual Studio, можно фирменной настройкой и распространением как свои собственные. Следующие разделы показывают, как приступить к работе с каждого типа модулей:  
  
-   Команды меню: [создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   Окна инструментов: [создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   Расширения редактора: [создания расширения с помощью редактора шаблона элемента](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   Основные VSPackages: [создание расширения с помощью VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   Шаблон проекта VSIX: [Приступая к работе с использованием шаблона проекта VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Visual Studio изолированной оболочки: [Пошаговое руководство: создание простого приложения изолированной оболочки](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Как получить расширение my выглядел как Visual Studio?  
 Полезные советы по разработке пользовательского интерфейса для расширения в [Visual Studio техники](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="where-can-i-find-examples-of-vssdk-code"></a>Где найти примеры кода, VSSDK  
 Пошаговые руководства, показывающие, как для реализации определенных функций, у каждого из ссылок, перечисленных в предыдущем разделе. Можно также найти открытого VSSDK примеры на GitHub в [примеры Visual Studio](https://aka.ms/vs2015sdksamples).  
  
## <a name="how-can-i-distribute-my-extension"></a>Как распределить расширения my  
 Можно установить расширение на другом компьютере или отправить его своим друзьям в VSIX-файл, который можно установить, дважды щелкнув его. Можно найти дополнительные сведения о пакетах VSIX в [доставки расширения Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Можно также опубликовать расширения в коллекции Visual Studio, который сделает ее видимой для большого количества пользователей Visual Studio. Пример упаковка расширения для коллекции, в разделе [Пошаговое руководство: публикация расширения Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Дополнительные сведения о то, что нужно сделать, чтобы опубликовать в коллекции, в разделе [продукты и расширения для Visual Studio](https://visualstudiogallery.msdn.microsoft.com/).
