---
title: Визуальная студия SDK Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56f772d7d27f11318cdeb0bf365373d5f7c1294b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698078"
---
# <a name="visual-studio-sdk"></a>SDK для Visual Studio
Visual Studio SDK поможет вам расширить функции Visual Studio или интегрировать новые функции в Visual Studio. Вы можете распространять свои расширения среди других пользователей, а также на Visual Studio Marketplace. Ниже перечислены некоторые из способов расширения Visual Studio:

- Добавление команд, кнопок, меню и других элементов uI в IDE

- Добавление окон инструментов для новой функциональности

- Расширить IntelliSense для данного языка или предоставить IntelliSense для новых языков программирования

- Используйте лампочки, чтобы предоставить подсказки и предложения, которые помогают разработчикам писать лучший код

- Включить поддержку нового языка

- Добавление пользовательского типа проекта

- Охватить миллионы разработчиков через Visual Studio Marketplace

  Если вы никогда не писали расширение Visual Studio раньше, вы должны найти более подробную информацию об этих функциях и на [начало разработки визуальных расширений studio.](../extensibility/starting-to-develop-visual-studio-extensions.md)

## <a name="install-the-visual-studio-sdk"></a>Установка пакета SDK для Visual Studio
 Визуальная студия SDK является дополнительной функцией в visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Что нового в Визуальной студии 2017 SDK
 Визуальная студия SDK имеет некоторые новые функции, такие как формат VSIX v3, а также нарушение изменений, которые могут потребовать от вас обновить расширение. Для получения дополнительной информации, смотрите [Что нового в Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).

## <a name="visual-studio-user-experience-guidelines"></a>Рекомендации по пользовательскому опыту Visual Studio
 Получите отличные советы по разработке пользовательского интерфейса для вашего расширения в [руководстве visual Studio пользовательского опыта.](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

 Вы также можете узнать, как сделать ваше расширение отлично выглядеть на устройствах с высоким DPI с [адресом DPI вопросы](../extensibility/addressing-dpi-issues2.md) статьи.

 Воспользуйтесь [сервисом и каталогом Image](../extensibility/image-service-and-catalog.md) для отличного управления изображениями и поддержки высокого DPI и тефеи.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Найти и установить существующие расширения Visual Studio
 Расширения Visual Studio можно найти в диалоге **расширений и обновлений** в меню **«Инструменты».** Для получения дополнительной информации смотрите [Поиск и использование визуальных расширений студии](../ide/finding-and-using-visual-studio-extensions.md). Вы также можете найти расширения в [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

## <a name="visual-studio-sdk-reference"></a>Визуальная студия SDK ссылка
 Вы можете найти Visual Studio SDK API ссылку на [Visual Studio SDK Ссылка](../extensibility/visual-studio-sdk-reference.md).

## <a name="visual-studio-sdk-samples"></a>Образцы Визуальной студии SDK
 Вы можете найти примеры с открытым исходным кодом расширения VS SDK на GitHub в [Visual Studio Samples.](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Это репо GitHub содержит образцы, которые иллюстрируют различные расширяемые функции в Visual Studio.

## <a name="other-visual-studio-sdk-resources"></a>Другие ресурсы Визуальной студии SDK
 Если у вас есть вопросы о VSSDK или вы хотите поделиться своим опытом разработки расширений, вы можете использовать [Visual Studio Расширение форума](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) или [ExtendVS Gitter Chatroom](https://gitter.im/Microsoft/extendvs).

 Вы можете найти более подробную информацию в [блоге VSX Arcana](https://blogs.msdn.microsoft.com/vsx/) и ряд блогов, написанных Microsoft MVPs:

- [Любимые расширения визуальной студии](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Расширяемость визуальной студии](http://www.visualstudioextensibility.com/overview/vs/)

- [Расширение визуальной студии](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>См. также

- [Создание расширения с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Как: Миграция расширяемости проектов Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [Часто задаваемые вопросы: Преобразование надстроек в расширения VSPackage](/visualstudio/extensibility/faq-converting-add-ins-to-vspackage-extensions?view=vs-2015)
- [Управление несколькими потоками в управляемом коде](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Расширить меню и команды](../extensibility/extending-menus-and-commands.md)
- [Добавление команд в панели инструментов](../extensibility/adding-commands-to-toolbars.md)
- [Расширение и настройка окон инструментов](../extensibility/extending-and-customizing-tool-windows.md)
- [Расширение службы редактора и языка](../extensibility/editor-and-language-service-extensions.md)
- [Расширение проектов](../extensibility/extending-projects.md)
- [Расширение настроек и параметров пользователя](../extensibility/extending-user-settings-and-options.md)
- [Создание пользовательских шаблонов проектов и элементов](../extensibility/creating-custom-project-and-item-templates.md)
- [Расширить свойства и окно свойства](../extensibility/extending-properties-and-the-property-window.md)
- [Расширить другие части Визуальной студии](../extensibility/extending-other-parts-of-visual-studio.md)
- [Использование и предоставление услуг](../extensibility/using-and-providing-services.md)
- [Управление пакетами VSPackage](../extensibility/managing-vspackages.md)
- [Визуальная студия изолированной оболочки](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Расширение визуальной студии ship](../extensibility/shipping-visual-studio-extensions.md)
- [Компоненты пакета SDK для Visual Studio](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Поддержка пакета SDK для Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)
- [Визуальная студия SDK ссылка](../extensibility/visual-studio-sdk-reference.md)
