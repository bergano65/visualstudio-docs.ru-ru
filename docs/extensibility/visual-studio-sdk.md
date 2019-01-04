---
title: Пакет SDK для Visual Studio | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26ac42cbcc70c34b221f1146bb0ba5314ca104dc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947752"
---
# <a name="visual-studio-sdk"></a>SDK для Visual Studio
Пакет SDK для Visual Studio поможет вам расширить возможности Visual Studio или интегрировать новые возможности в Visual Studio. Вы можете предоставлять свои расширения другим пользователям, а также в Visual Studio Marketplace. Ниже перечислены некоторые из способов расширения Visual Studio:  
  
- Добавление команд, кнопки, меню и других элементов пользовательского интерфейса в интегрированную среду разработки  
  
- Как добавить окна средств для новых функциональных возможностей  
  
- Расширения IntelliSense для данного языка и обеспечивает поддержку технологии IntelliSense для новых языков программирования  
  
- Использование значка лампочки для предоставления подсказки и рекомендации, помогающие разработчикам создавать более качественные приложения  
  
- Включить поддержку нового языка  
  
- Добавление пользовательского типа проекта  
  
- Миллионы разработчиков с помощью Visual Studio Marketplace  
  
  Если вы не написали ни расширение Visual Studio, прежде чем, вы увидите Дополнительные сведения об этих функциях, а также в [Приступая к разработке расширений Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="install-the-visual-studio-sdk"></a>Установка пакета SDK для Visual Studio  
 Пакет SDK для Visual Studio является дополнительным компонентом в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Новые возможности пакета SDK для Visual Studio 2017  
 Пакет SDK для Visual Studio имеет некоторые новые функции, такие как формат VSIX v3, а также критические изменения, которые может потребоваться обновить расширение. Дополнительные сведения см. в разделе [новые возможности в Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>По работе пользователей Visual Studio  
 Полезные советы по проектированию пользовательского интерфейса для расширения в [рекомендации по пользовательскому интерфейсу Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Вы также узнаете, как осуществлять расширение отлично выглядят на высоким значением dpi с [выдает DPI адрес](../extensibility/addressing-dpi-issues2.md) статьи.  
  
 Воспользоваться преимуществами [изображения каталог и служба](../extensibility/image-service-and-catalog.md) управления отличный образами и поддержку высокое разрешение и темы.  
  
## <a name="find-and-install-existing-visual-studio-extensions"></a>Найти и установить существующие расширения Visual Studio  
 Вы найдете расширений Visual Studio в **расширения и обновления** диалоговое окно на **средства** меню. Дополнительные сведения см. в разделе [поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Также можно найти расширения в [Visual Studio marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Справочник по Visual Studio SDK  
 Вы найдете ссылку на API пакета SDK для Visual Studio по [Справочник по Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Примеры Visual Studio SDK  
 Примеры открытым исходным кодом расширений VS SDK можно найти на сайте GitHub в [примеры Visual Studio](https://aka.ms/vs2015sdksamples). Этот репозиторий GitHub содержит примеры, демонстрирующие различные расширяемые возможности в Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Другие ресурсы пакета SDK для Visual Studio  
 Если у вас вопросы о VSSDK или хотите поделиться опытом разработки расширений, можно использовать [форум расширяемости Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) или [комнаты чата Gitter ExtendVS](https://gitter.im/Microsoft/extendvs).  
  
 Дополнительные сведения в [VSX Arcana блог](https://blogs.msdn.microsoft.com/vsx/) и ряд блогов, написанные специалистами MVP:  
  
-   [Избранные расширения Visual Studio](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Расширяемость Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Расширение Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>См. также  
 [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Практическое руководство. Перенос проектов расширяемости в Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [ВОПРОСЫ И ОТВЕТЫ: Преобразование надстроек в расширения VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Управление несколькими потоками в управляемом коде](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)   
 [Добавление команды на панели инструментов](../extensibility/adding-commands-to-toolbars.md)   
 [Расширение и настройка окон инструментов](../extensibility/extending-and-customizing-tool-windows.md)   
 [Редактор и языковой службы расширения](../extensibility/editor-and-language-service-extensions.md)   
 [Расширения проектов](../extensibility/extending-projects.md)   
 [Расширить пользовательские настройки и параметры](../extensibility/extending-user-settings-and-options.md)   
 [Создание пользовательских шаблонов проектов и элементов](../extensibility/creating-custom-project-and-item-templates.md)   
 [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md)   
 [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Использование и предоставление служб](../extensibility/using-and-providing-services.md)   
 [Управление пакетов VSPackage](../extensibility/managing-vspackages.md)   
 [Visual Studio изолированной оболочки](/visualstudio/extensibility/shell/visual-studio-isolated-shell)   
 [Поставлять расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Внутри Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Поддержка пакета SDK для Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Архив](../extensibility/archive.md)   
 [Справочник по Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
