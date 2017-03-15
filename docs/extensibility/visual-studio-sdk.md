---
title: "Пакет SDK для Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 56
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
ms.sourcegitcommit: 477f57bbca9c49e7d7d13155fc1f6e55ee4667a8
ms.openlocfilehash: efc5a2722757229057a91f5e3a6c2ad3681f5a89
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-sdk"></a>SDK для Visual Studio
Visual Studio SDK позволяет расширить возможности Visual Studio или интегрировать новые возможности в Visual Studio. Можно распределить расширений для других пользователей, а также в коллекции Visual Studio. Ниже перечислены некоторые из способов расширения Visual Studio:  
  
-   Добавление команд, кнопки, меню и других элементов пользовательского интерфейса интегрированной среды разработки  
  
-   Как добавить окна средств для новых функциональных возможностей  
  
-   Расширение IntelliSense для данного языка или предоставить IntelliSense для новых языков программирования  
  
-   Использовать для предоставления советы и рекомендации, помогающие разработчикам писать лучший код лампочки  
  
-   Включение поддержки нового языка  
  
-   Добавление пользовательского типа проектов  
  
-   Миллионам разработчиков с помощью коллекции Visual Studio  
  
 Если вам не доводилось писать расширение до Visual Studio, вы должны найти дополнительные сведения об этих возможностях, а также в [начинает разрабатывать расширения Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Установка Visual Studio SDK  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Новые возможности пакета SDK для Visual Studio 2015 г.  
 Пакет SDK для Visual Studio содержит ряд новых возможностей, включая лампочки и новых элементов проекта, которые позволяют создавать команды меню, окна инструментов и расширения редактора, с помощью пакета VSIX. Дополнительные сведения см. в разделе [новые возможности Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Руководство по работе пользователей Visual Studio  
 Полезные советы по разработке пользовательского интерфейса для расширения в [Visual Studio техники](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Также узнайте, как осуществлять расширение выглядеть очень высоким DPI устройствами с помощью наших [адресации проблем DPI](../extensibility/addressing-dpi-issues2.md) раздела.  
  
 Воспользоваться преимуществами [систему обслуживания образов и каталога](../extensibility/image-service-and-catalog.md) для управления образами полезные и поддержку высокого Разрешения и тем.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Поиск и установка существующие расширения Visual Studio  
 Можно найти расширения Visual Studio в **расширения и обновления** диалоговое окно на **средства** меню. Дополнительные сведения см. в разделе [поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Также можно найти расширения в [коллекции Visual Studio](https://visualstudiogallery.msdn.microsoft.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Справочник по Visual Studio SDK  
 Можно найти ссылку на API пакета SDK для Visual Studio по [Справочник по языку Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Примеры Visual Studio SDK  
 Примеры открытого VS SDK расширений можно найти на GitHub в [примеры Visual Studio](https://aka.ms/vs2015sdksamples). Этот репозиторий GitHub содержит примеры, демонстрирующие различные возможности расширенного в Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Другие ресурсы пакета SDK для Visual Studio  
 При наличии вопросов по VSSDK или хотите поделиться опытом разработки расширений, можно использовать [форум расширяемости Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) или [ExtendVS Group Chat](https://gitter.im/Microsoft/extendvs).  
  
 Можно найти дополнительные сведения об [VSX Arcana блог](http://blogs.msdn.com/b/vsx/) и количество блогов, написанные специалистами MVP:  
  
-   [Расширения Visual Studio избранного](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Расширение возможностей Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Расширение Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>См. также  
 [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Практическое руководство: перенести проекты расширения среды Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [Часто задаваемые вопросы: Преобразование надстроек в расширения VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Управление несколькими потоками в управляемом коде](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)   
 [Добавление команд на панели инструментов](../extensibility/adding-commands-to-toolbars.md)   
 [Расширение и настройка окна инструментов](../extensibility/extending-and-customizing-tool-windows.md)   
 [Редактор и расширения службы языка](../extensibility/editor-and-language-service-extensions.md)   
 [Расширение проектов](../extensibility/extending-projects.md)   
 [Расширение настройки пользователя и параметры](../extensibility/extending-user-settings-and-options.md)   
 [Создание настраиваемого проекта и шаблоны элементов](../extensibility/creating-custom-project-and-item-templates.md)   
 [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md)   
 [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Использование и предоставления услуг](../extensibility/using-and-providing-services.md)   
 [Управление пакеты VSPackage](../extensibility/managing-vspackages.md)   
 [Visual Studio изолированной оболочки](../extensibility/visual-studio-isolated-shell.md)   
 [Расширения Visual Studio доставки](../extensibility/shipping-visual-studio-extensions.md)   
 [В Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Поддержка Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Архив](../extensibility/archive.md)   
 [Справочник по Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
