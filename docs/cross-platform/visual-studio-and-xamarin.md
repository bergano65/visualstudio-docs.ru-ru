---
title: Visual Studio и Xamarin | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
caps.latest.revision: ''
author: asb3993
ms.author: amburns
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: a6ac102244f52d5ca33e40bd7500a19cbcd8b28d
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio и Xamarin
Xamarin — это платформа разработки мобильных приложений для создания нативных приложений iOS, Android и Windows из общего кода C# или .NET, которая позволяет многократно использовать между платформами от 75 % до почти 100 % кода. Приложения, написанные с помощью Xamarin и C#, имеют полный доступ к интерфейсам API базовой платформы и возможность создавать собственные пользовательские интерфейсы, а также компилировать код в пакеты конкретных платформ, поэтому влияние на производительность во время выполнения является незначительным. (Примечание. Xamarin также поддерживает F#, но в этой документации основное внимание уделяется C#. Visual Basic пока не поддерживается.)  
  
 Разработчики, знакомые с C#, .NET и Visual Studio, могут рассчитывать на такие же возможности и производительность при работе с Xamarin для мобильных приложений, включая удаленную отладку на устройствах Android, iOS и Windows, без необходимости изучать нативные языки, например Objective-C или Java. Удивительно, но много высокопроизводительных приложений с красивыми пользовательскими интерфейсами например, NASCAR, Aviva и MixRadio, созданы с помощью Xamarin.  
  
 Эта документация поможет оценить все возможности **Visual Studio с Xamarin** для создания указанных ниже решений.  
  
-   Начните с раздела [Настройка и установка](../cross-platform/setup-and-install.md) — это может занять некоторое время (обычно 2–4 часа в зависимости от скорости подключения к Интернету, уже установленных компонентов и выбранных параметров).  
  
-   Во время выполнения установщиков вы можете изучить раздел [Подробности о разработке мобильных приложений с использованием Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md), где описан характер работы Xamarin, дано сравнение Xamarin.Forms и собственного пользовательского интерфейса, а также приведено много других данных.  
  
-   После завершения установки прочитайте раздел [Проверка окружения Xamarin](../cross-platform/verify-your-xamarin-environment.md).  
  
-   В завершение ознакомьтесь с учебником [Основы создания приложений с помощью Xamarin.Forms в Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).  
  
 Вы можете использовать все функции Xamarin в [любом выпуске Visual Studio 2015](https://www.visualstudio.com/vs-2015-product-editions) (Community, Professional и Enterprise). Начиная с 31 марта 2016 года, Xamarin включается во все выпуски Visual Studio 2015 и больше не требует отдельной лицензии. Для Visual Studio 2013 можно установить Xamarin отдельно, как описано в разделе [Настройка и установка](../cross-platform/setup-and-install.md).  
  
> [!NOTE]
>  Эти инструкции описывают самую простую и очевидную конфигурацию компьютера для тех, кто имеет опыт работы с Windows и Visual Studio. При использовании этой конфигурации разработка упрощается, так как необходимо взаимодействовать с Mac только для того, чтобы использовать симулятор iOS и связанное устройство. Если же вы используете Mac, рекомендуется запустить Visual Studio в Parallels или VMWare либо использовать Xamarin Studio Community. Инструкции см. в разделе [Программа установки, установка и проверки для пользователей Mac](../cross-platform/setup-install-and-verifications-for-mac-users.md).  
  
> [!NOTE]
>  Если вы ищете решение для кроссплатформенной разработки на основе HTML и CSS, ознакомьтесь с инструментами Visual Studio для Apache Cordova, описанными в разделе [Кроссплатформенная разработка в Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML).