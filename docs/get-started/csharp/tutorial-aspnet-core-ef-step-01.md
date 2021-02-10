---
title: Создание веб-приложения ASP.NET Core с помощью Visual Studio 2019 и Entity Framework
titleSuffix: ''
description: Получение сведений из видеоучебника и пошаговых инструкций по установке Visual Studio 2019 является первым шагом на пути к созданию веб-приложения ASP.NET Core.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: c6cf4429607f8ceb2a3ed4a5a1cb91274a201698
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922804"
---
# <a name="tutorial-create-your-first-aspnet-core-app-using-entity-framework-with-visual-studio-2019"></a>Учебник. Создайте первое приложение ASP.NET Core с помощью Entity Framework в Visual Studio 2019

Из этого руководства вы узнаете, как создать веб-приложение ASP.NET Core, использующее данные, и развернуть его в Azure. Данное руководство состоит из следующих шагов.

- [Шаг 1. Установка Visual Studio 2019.](#step-1-install-visual-studio-2019)
- [Шаг 2. Создание первого веб-приложения ASP.NET Core.](tutorial-aspnet-core-ef-step-02.md)
- [Шаг 3. Работа с данными с использованием Entity Framework.](tutorial-aspnet-core-ef-step-03.md)
- [Шаг 4. Предоставление веб-API приложения ASP.NET Core.](tutorial-aspnet-core-ef-step-04.md)
- [Шаг 5. Развертывание приложения ASP.NET в Azure.](tutorial-aspnet-core-ef-step-05.md)

## <a name="step-1-install-visual-studio-2019"></a>Шаг 1. Установка Visual Studio 2019

В этом видеоучебнике и пошаговых инструкциях приведены сведения об установке Visual Studio 2019. Если вы уже установили Visual Studio, перейдите к статье [Step 2: Create your first ASP.NET Core web app](tutorial-aspnet-core-ef-step-02.md) (Шаг 2. Создание первого веб-приложения ASP.NET CoreVisual Studio).

_Выполните инструкции из этого видео, чтобы установить Visual Studio и создать первое приложение ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/Fz_HAqQGLtY]

## <a name="download-the-installer"></a>Скачивание установщика

Чтобы найти установщик, перейдите на [visualstudio.com](https://visualstudio.com). Найдите ссылку на Visual Studio 2019 и щелкните ее, чтобы начать загрузку. Чтобы получить бесплатную версию Visual Studio, выберите Visual Studio Community.

## <a name="start-the-installer"></a>Запуск установщика

Чтобы запустить установщик, после завершения загрузки щелкните **Выполнить**.

![Установщик Visual Studio 2019](media/vs-2019/vs2019-installer.png)

## <a name="choose-workloads"></a>Выбор рабочих нагрузок

Visual Studio можно использовать для различных типов разработки, а рабочие нагрузки позволяют более легко выполнять загрузку компонентов, необходимых для создания приложений. На данный момент выберите такие рабочие нагрузки, как **ASP.NET и разработка веб-приложений** и **Кроссплатформенная разработка .NET Core**. Чтобы установить дополнительные компоненты и рабочие нагрузки, вы всегда можете повторно запустить установщик позднее.

![Выбор рабочих нагрузок в Visual Studio 2019](media/vs-2019/vs2019-choose-workloads.png)

## <a name="install"></a>Установка

Щелкните **Установка**. После этого установщик загрузит и установит Visual Studio.

## <a name="run-visual-studio-for-the-first-time"></a>Первый запуск Visual Studio

Visual Studio должен автоматически запуститься после завершения установки. Может появиться запрос на выполнение входа, так как это связано с некоторыми удобными функциями, но на данном этапе это действие можно пропустить. Затем необходимо выбрать тему и параметры разработки. Выполнив этот выбор, вы можете начать свой первый проект. Последовательно выберите **Создание нового проекта** и **Веб-приложение ASP.NET Core**.

![Создание нового проекта веб-приложения ASP.NET Core в Visual Studio 2019](media/vs-2019/vs2019-create-new-project.png)

## <a name="explore-aspnet-core-project-types"></a>Просмотр типов проектов ASP.NET Core

Выберите имя и расположение проекта и щелкните **Создать**. Теперь выберите шаблон, который будет использоваться в приложении ASP.NET Core. Можно выбрать один из следующих вариантов.

- Пустой. Шаблон пустого проекта позволяет вам начать с нуля.
- API. Лучше подходит для веб-API.
- Веб-приложение. Стандартное веб-приложение ASP.NET Core, созданное с помощью Razor Pages.
- Веб-приложение (модель-представление-контроллер). Стандартное веб-приложение ASP.NET Core, в котором используется шаблон модель-представление-контроллер.
- Angular.
- React.js.
- React.js / Redux.
- Библиотека классов Razor. Используется для предоставления общего доступа к ресурсам Razor в разных проектах.

Обратите внимание, что если установить флажок в поле включения поддержки Docker, то можно выбрать большинство шаблонов проектов. Также если нажать кнопку "Проверка подлинности", можно добавить поддержку проверки подлинности. Здесь доступны следующие варианты.

- Без поверки подлинности.
- Учетные записи отдельных пользователей. Они хранятся в локальной базе данных или базе данных Azure.
- Рабочие или учебные учетные записи. В этом параметре для аутентификации используется Active Directory, Azure AD или Microsoft 365.
- Проверка подлинности Windows. Подходит для приложений интрасети.

Выберите стандартный шаблон веб-приложения без проверки подлинности и нажмите кнопку **Создать**.

![Выбор параметров проекта ASP.NET Core в Visual Studio 2019](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="next-steps"></a>Следующие шаги

Из следующего видео вы узнаете больше о первом проекте ASP.NET Core.

[Учебник. Создание первого веб-приложения ASP.NET Core](tutorial-aspnet-core-ef-step-02.md)

## <a name="see-also"></a>См. также

- [Учебник. Начало работы с C# и ASP.NET Core в Visual Studio](tutorial-aspnet-core.md). Здесь приведено более подробное руководство без пошаговых видеоуроков.
