---
title: Visual Studio и Xamarin | Документы Майкрософт
ms.custom: ''
ms.date: 03/30/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: caf1ea462cc69366f11e4768003707e9cc263327
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495743"
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio и Xamarin

Xamarin — это платформа разработки мобильных приложений для создания собственных приложений iOS, Android и Windows из общего кода C# или .NET. В приложениях, написанных при помощи Xamarin, повторное использование кода между разными платформами достигает от 75 % до почти 100 %. Эти приложения имеют полный доступ к интерфейсам API базовых платформ и могут использовать собственные пользовательские интерфейсы. Приложения компилируются в пакеты под конкретную платформу, при этом влияние на производительность во время выполнения остается незначительным. (Примечание. Xamarin также поддерживает F#, но в этой документации основное внимание уделяется C#. Visual Basic пока не поддерживается.)

Разработчики, знакомые с C#, .NET и Visual Studio, могут рассчитывать на те же возможности и производительность при работе с Xamarin для мобильных приложений. К этим преимуществам относятся удаленная отладка на устройствах Android, iOS и Windows без необходимости изучения собственных языков программирования, таких как Objective-C или Java. Удивительно, но много высокопроизводительных приложений с красивыми пользовательскими интерфейсами, например NASCAR, Aviva и MixRadio, созданы с помощью Xamarin.

Эта документация поможет оценить всю мощь **Visual Studio с Xamarin** для создания указанных ниже решений.

-   Начните с [Setup and install](../cross-platform/setup-and-install.md)— процесса, который может занять некоторое время (обычно 2–4 часа в зависимости от скорости подключения к Интернету, уже установленных компонентов и выбранных параметров).

-   Во время выполнения установщиков вы можете изучить раздел [Подробности о разработке мобильных приложений с использованием Xamarin](learn-about-mobile-development-with-xamarin.md), где описан характер работы Xamarin, дано сравнение Xamarin.Forms и собственного пользовательского интерфейса, а также приведено много других данных.

-   После завершения установки прочитайте раздел [Проверка окружения Xamarin](../cross-platform/verify-your-xamarin-environment.md).

-   В завершение ознакомьтесь с учебником [Основы создания приложений с помощью Xamarin.Forms в Visual Studio](learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).

Вы можете использовать все функции Xamarin в [любом выпуске Visual Studio 2017](https://visualstudio.microsoft.com/vs) (Community, Professional и Enterprise). Дополнительных лицензий не требуется.

> [!NOTE]
>  Эти инструкции описывают самую простую и очевидную конфигурацию компьютера для разработчиков, которые имеют опыт работы с Windows и Visual Studio. При использовании этой конфигурации разработка упрощается, так как необходимо взаимодействовать с Mac только для того, чтобы использовать симулятор iOS и связанные устройства. Если же вы используете Mac, рекомендуется запустить Visual Studio в Parallels или VMWare либо использовать Visual Studio для Mac. Инструкции см. в разделе [Программа установки, установка и проверки для пользователей Mac](../cross-platform/setup-install-and-verifications-for-mac-users.md).

> [!NOTE]
>  Если вы ищете решение для кроссплатформенной разработки на основе HTML и CSS, ознакомьтесь с инструментами Visual Studio для Apache Cordova, описанными в разделе [Кроссплатформенная разработка в Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML).