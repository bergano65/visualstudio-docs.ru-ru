---
title: "Пакет SDK для Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: "56"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bf8c558d01538d477aee3670b3c119d72a83878d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-sdk"></a>SDK для Visual Studio
Пакет SDK для Visual Studio позволяет расширить возможности Visual Studio или интегрировать новые возможности в Visual Studio. Вы можете предоставлять свои расширения другим пользователям, а также с Visual Studio Marketplace. Ниже перечислены некоторые из способов расширения Visual Studio:  
  
-   Добавление команд, кнопки, меню и других элементах пользовательского интерфейса в интегрированную среду разработки  
  
-   Добавлять окна инструментов для новых функциональных возможностей  
  
-   Расширение IntelliSense для данного языка или IntelliSense для новых языков программирования  
  
-   Использовать лампочки для предоставления советы и рекомендации, помогающие разработчикам написание кода  
  
-   Включить поддержку нового языка  
  
-   Добавление пользовательского типа проектов  
  
-   Миллионам разработчиков через Visual Studio Marketplace  
  
 Если не вы написали расширение Visual Studio до, вы должны найти дополнительные сведения об этих функциях, а также в [начинается разработка расширений Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Установка Visual Studio SDK  
 Пакет SDK для Visual Studio является дополнительным компонентом в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Новые возможности Visual Studio SDK 2017 г.  
 Пакет SDK для Visual Studio имеет некоторые новые возможности, такие как формат VSIX v3, а также критические изменения, которые могут потребовать обновления модуля. Дополнительные сведения см. в разделе [новые возможности Visual Studio SDK 2017 г](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Рекомендации по пользовательскому интерфейсу Visual Studio  
 Получить советы по проектированию пользовательского интерфейса для расширения в [Visual Studio техники](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Также можно узнать, как делать расширение выглядеть очень высоким DPI устройствами с помощью наших [адресации проблемах с DPI](../extensibility/addressing-dpi-issues2.md) раздела.  
  
 Воспользоваться преимуществами [служба образов и каталога](../extensibility/image-service-and-catalog.md) управления большие изображения и поддержку высокое разрешение и темы.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Поиск и установка существующие расширения Visual Studio  
 Можно найти расширений Visual Studio в **расширения и обновления** диалоговое окно для **средства** меню. Дополнительные сведения см. в разделе [Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Также можно найти расширения в [Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Справочник по SDK для Visual Studio  
 Можно найти ссылку на API пакета SDK для Visual Studio по [Справочник по Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Примеры Visual Studio SDK  
 Примеры открытой VS SDK расширений можно найти на github на сайте [примеры Visual Studio](https://aka.ms/vs2015sdksamples). В репозитории GitHub содержит образцы, демонстрирующие различные возможности расширенного в Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Другие ресурсы для пакета SDK Visual Studio  
 При наличии вопросов по VSSDK или хотите поделиться своим опытом разработки расширений, можно использовать [форум расширяемости Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) или [ExtendVS Gitter Chatroom](https://gitter.im/Microsoft/extendvs).  
  
 Можно найти дополнительные сведения в [VSX Arcana блог](http://blogs.msdn.com/b/vsx/) и ряд блогов, написанном MVP:  
  
-   [Расширения избранные Visual Studio](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Расширение возможностей Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Расширение Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>См. также  
 [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Как: переноса расширяемости проектов в Visual Studio 2017 г.](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [Часто задаваемые вопросы: Преобразование надстроек для расширений VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Управление несколькими потоками в управляемом коде](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)   
 [Добавление команд на панели инструментов](../extensibility/adding-commands-to-toolbars.md)   
 [Расширение и настройка окна инструментов](../extensibility/extending-and-customizing-tool-windows.md)   
 [Редактор и расширения службы языка](../extensibility/editor-and-language-service-extensions.md)   
 [Расширение проектов](../extensibility/extending-projects.md)   
 [Расширение настройки пользователя и параметры](../extensibility/extending-user-settings-and-options.md)   
 [Создание пользовательских проектов и шаблонов элементов](../extensibility/creating-custom-project-and-item-templates.md)   
 [Расширение свойств и в окне свойств](../extensibility/extending-properties-and-the-property-window.md)   
 [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Использование и предоставления услуг](../extensibility/using-and-providing-services.md)   
 [Управление пакетов VSPackage](../extensibility/managing-vspackages.md)   
 [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)   
 [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [В среде Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Поддержка Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Архив](../extensibility/archive.md)   
 [Справочник по пакету SDK для Visual Studio](../extensibility/visual-studio-sdk-reference.md)
