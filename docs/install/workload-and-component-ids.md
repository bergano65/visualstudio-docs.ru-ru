---
title: Идентификаторы рабочих нагрузок и компонентов Visual Studio 2017 | Документация Майкрософт
description: Идентификаторы рабочих нагрузок и компонентов позволяют устанавливать Visual Studio с помощью командной строки. Также их можно указать в качестве зависимости в манифесте VSIX
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 03/05/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.technology:
- vs-acquisition
ms.assetid: 34e19ef1-abfb-44fd-aad2-33c5d7874482
ms.workload:
- multiple
ms.openlocfilehash: 46450ab0b4c98f6d8155e71433a40e61464d792b
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/03/2018
---
# <a name="visual-studio-2017-workload-and-component-ids"></a>Идентификаторы рабочих нагрузок и компонентов Visual Studio 2017
Щелкайте имена выпусков в таблице ниже, чтобы увидеть идентификаторы доступных рабочих нагрузок и компонентов, которые нужны для установки Visual Studio из командной строки или для определения в качестве зависимости в манифесте VSIX.

| **Выпуск** | **ID** | **Описание** |
| ----------- | ------ | --------------- |
| [Visual&nbsp;Studio Enterprise&nbsp;2017](workload-component-id-vs-enterprise.md) | Microsoft.VisualStudio.Product.Enterprise | Разработанное Майкрософт решение DevOps для повышения производительности труда и координации в командах любого размера |
| [Visual&nbsp;Studio Professional&nbsp;2017](workload-component-id-vs-professional.md) | Microsoft.VisualStudio.Product.Professional | Профессиональные инструменты и службы для разработки, предназначенные для небольших команд |
| [Visual&nbsp;Studio Community&nbsp;2017](workload-component-id-vs-community.md) | Microsoft.VisualStudio.Product.Community | Бесплатная полнофункциональная интегрированная среда разработки для учащихся, разработчиков открытого ПО и индивидуальных разработчиков |
| [Visual&nbsp;Studio Team&nbsp;Explorer&nbsp;2017](workload-component-id-vs-team-explorer.md) | Microsoft.VisualStudio.Product.TeamExplorer | Обеспечивает взаимодействие с Team Foundation Server и Visual Studio Team Services без набора инструментов разработки Visual Studio |
| [Visual Studio Desktop Express 2017](workload-component-id-vs-express.md) | Microsoft.VisualStudio.Workload.WDExpress | Сборка собственных и управляемых приложений, таких как WPF, WinForms и Win32 с возможностью редактирования кода с учетом синтаксиса, а также управления исходным кодом и рабочими элементами. Включает поддержку C#, Visual Basic и Visual C++. |
| [Visual&nbsp;Studio Build&nbsp;Tools&nbsp;2017](workload-component-id-vs-build-tools.md) | Microsoft.VisualStudio.Product.BuildTools | Visual Studio Build Tools позволяют создавать приложения в машинном и управляемом коде на основе MSBuild без использования интегрированной среды разработки Visual Studio. Также можно установить компиляторы и библиотеки Visual C++, ATL, MFC, а также поддержку C++ и интерфейса командной строки. |
| [Агент&nbsp;тестирования&nbsp;Visual&nbsp;Studio 2017](workload-component-id-vs-test-agent.md)  | Microsoft.VisualStudio.Product.TestAgent | Поддерживает удаленное выполнение автоматических и нагрузочных тестов |
| [Visual&nbsp;Studio Test&nbsp;Controller 2017](workload-component-id-vs-test-controller.md) | Microsoft.VisualStudio.Product.TestController | Распределение автоматических тестов на несколько компьютеров |
| [Visual&nbsp;Studio Test&nbsp;Professional&nbsp;2017](workload-component-id-vs-test-professional.md) | Microsoft.VisualStudio.Product.TestProfessional | Visual Studio Test Professional 2017 |
| [Visual&nbsp;Studio Feedback&nbsp;Client&nbsp;2017](workload-component-id-vs-feedback-client.md) | Microsoft.VisualStudio.Product.FeedbackClient | Visual Studio Feedback Client 2017 |

Дополнительные сведения об использовании этих списков см. в статьях [Использование параметров командной строки для установки Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) и [Руководство по переносу проектов расширяемости в Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="get-support"></a>Техническая поддержка
Иногда возникают проблемы. При сбое установки Visual Studio см. инструкции по [устранению неполадок и исправлению ошибок установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md). Если описанные выше действия не устраняют проблему, вы можете обратиться к нам за помощью в чате в реальном времени (только на английском языке). Дополнительные сведения см. на [странице поддержки Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ниже приведены несколько дополнительных вариантов:
* Вы можете сообщить о проблемах с продуктом в корпорацию Майкрософт, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Оно доступно как в Visual Studio Installer, так и в Visual Studio IDE.
* Вы можете оставить предложение о продукте на форуме [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Вы можете просматривать описания проблем в [сообществе разработчиков Visual Studio](https://developercommunity.visualstudio.com/). Там же можно получать ответы на интересующие вас вопросы.
* Вы также можете связаться с нами и другими разработчиками Visual Studio, используя [средство для обсуждения Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio).  (Требуется учетная запись [GitHub](https://github.com/).)

## <a name="see-also"></a>См. также
* [Руководство администратора Visual Studio 2017](visual-studio-administrator-guide.md)
* [Создание автономной установки Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Примеры параметров командной строки для установки Visual Studio 2017](command-line-parameter-examples.md)
