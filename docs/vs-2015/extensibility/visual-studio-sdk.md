---
title: Пакет SDK для Visual Studio | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 57
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 27dce16d9fe02063eae935af96c26184285e583d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850370"
---
# <a name="visual-studio-sdk"></a>SDK для Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пакет SDK для Visual Studio помогает расширить возможности Visual Studio или интегрировать новые функции в Visual Studio. Вы можете распространять расширения для других пользователей, а также для коллекции Visual Studio. Ниже перечислены некоторые из способов расширения Visual Studio:  
  
- Добавление команд, кнопок, меню и других элементов пользовательского интерфейса в интегрированную среду разработки  
  
- Добавление окон инструментов для новых функциональных возможностей  
  
- Расширение IntelliSense для данного языка или обеспечение IntelliSense для новых языков программирования  
  
- Используйте лампочки, чтобы предоставить подсказки и предложения, помогающие разработчикам писать более подходящий код.  
  
- Включить поддержку для нового языка  
  
- Добавление пользовательского типа проекта  
  
- Достигайте миллионов разработчиков с помощью Visual Studio Marketplace  
  
  Если вы ранее не записали расширение Visual Studio, то получите дополнительные сведения об этих функциях и [Начните разработку расширений Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Установка пакета SDK для Visual Studio  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Новые возможности пакета SDK для Visual Studio 2015  
 Пакет SDK для Visual Studio содержит некоторые новые функции, включая лампочки и новые элементы проекта, позволяющие создавать команды меню, окна инструментов и расширения редактора с помощью пакета VSIX. Дополнительные сведения см. [в разделе новые возможности пакета SDK для Visual Studio 2015](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Руководство по работе пользователей Visual Studio  
 Получите советы по проектированию пользовательского интерфейса для расширения в [руководстве пользователя Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Вы также можете узнать, как сделать расширение более удобным на устройствах с высоким разрешением, выполнив наши [проблемы с адресацией dpi](../extensibility/addressing-dpi-issues2.md) .  
  
 Воспользуйтесь [службой образов и каталогом](../extensibility/image-service-and-catalog.md) , чтобы получить превосходные возможности управления образами и поддержки высокого DPI.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Поиск и установка существующих расширений Visual Studio  
 Расширения Visual Studio можно найти в диалоговом окне **расширения и обновления** в меню **Сервис** . Дополнительные сведения см. в разделе [Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Расширения можно также найти в [Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Справочник по пакету SDK для Visual Studio  
 Справочник по API пакета SDK для Visual Studio можно найти в [справочнике по Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Примеры пакета SDK для Visual Studio  
 Примеры Open Source для расширений VS SDK можно найти на сайте GitHub в [примерах Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Этот репозиторий GitHub содержит примеры, иллюстрирующие различные Расширяемые функции в Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Другие ресурсы пакета SDK для Visual Studio  
 Если у вас есть вопросы о VSSDK или хотите поделиться опытом разработки расширений, вы можете использовать [форум по расширению Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) или [чат екстендвс Group Chat](https://gitter.im/Microsoft/extendvs).  
  
 Дополнительные сведения см. в [блоге Аркана по VSX](https://blogs.msdn.microsoft.com/vsx/) , а также в нескольких блогах, созданных специалистами MVP корпорации Майкрософт:  
  
- [Избранные расширения Visual Studio](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)  
  
- [Расширяемость Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
- [Расширение Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>См. также раздел  
 [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Как перенести проекты расширяемости в Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [Часто задаваемые вопросы: преобразование надстроек в расширения VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Управление несколькими потоками в управляемом коде](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)   
 [Добавление команд в панели инструментов](../extensibility/adding-commands-to-toolbars.md)   
 [Расширение и настройка окон инструментов](../extensibility/extending-and-customizing-tool-windows.md)   
 [Расширения редактора и языковой службы](../extensibility/editor-and-language-service-extensions.md)   
 [Расширение проектов](../extensibility/extending-projects.md)   
 [Расширение параметров пользователя и параметров](../extensibility/extending-user-settings-and-options.md)   
 [Создание пользовательских шаблонов проектов и элементов](../extensibility/creating-custom-project-and-item-templates.md)   
 [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md)   
 [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Использование и предоставление служб](../extensibility/using-and-providing-services.md)   
 [Расширение Подключенные службы](../extensibility/extending-connected-services.md)   
 [Управление](../extensibility/managing-vspackages.md) пакетами VSPackage   
   [изолированной оболочки Visual Studio](../extensibility/visual-studio-isolated-shell.md)  
 [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 В [пакете SDK для Visual Studio](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Поддержка пакета SDK для Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)   
   [архива](../extensibility/archive.md)  
 [Справочник по пакету SDK для Visual Studio](../extensibility/visual-studio-sdk-reference.md)
