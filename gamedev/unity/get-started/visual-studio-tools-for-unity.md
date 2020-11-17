---
title: Инструменты Visual Studio для Unity | Документация Майкрософт
description: Ознакомьтесь с обзором Инструментов Visual Studio для Unity, которые представляют собой бесплатное расширение Visual Studio, помогающее разрабатывать кроссплатформенные игры и приложения с помощью Unity.
ms.custom: ''
ms.date: 10/25/2019
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: overview
ms.assetid: 6cabc626-5310-4622-a743-210a9abb5535
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: ee4e9e0dc9df4eb5decb3fc9c2afb0411e9cb75c
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2020
ms.locfileid: "93405406"
---
# <a name="visual-studio-tools-for-unity"></a>Набор средств Visual Studio для Unity
![Набор средств Visual Studio для Unity](../media/hero.png)

## <a name="overview"></a>Обзор
Инструменты Visual Studio для Unity представляют собой бесплатное расширение Visual Studio, которое превращает Visual Studio в мощное средство для разработки кроссплатформенных игр и приложений с помощью платформы Unity.

Редактор Unity отлично подходит для объединения вашей игровой среды, но непосредственно в нем создавать код нельзя. Благодаря набору средств Инструментов Visual Studio для Unity можно использовать знакомые возможности среды Visual Studio редактирования, отладки и повышения производительности кода, чтобы создавать редактор и игровые скрипты для проекта Unity на C#, а также отлаживать их с помощью мощных средств отладки Visual Studio.

Однако набор средств Visual Studio Tools для Unity не ограничивается только вышеперечисленным. Он также тесно интегрирован с редактором Unity, что позволяет тратить меньше времени на выполнение простых задач, обеспечивает повышение производительности, характерное для Unity, а также делает очень удобной работу с документацией по Unity.

### <a name="compatible-with-visual-studio-community-on-windows-and-macos-and-bundled-with-unity"></a>Совместимость с Visual Studio Community в Windows и macOS и объединение с Unity
Visual Studio и Visual Studio для Mac Community доступна бесплатно и входит в пакет установки Unity. Дополнительные сведения об установке и настройке см. в статье [Начало работы с инструментами Visual Studio для Unity](getting-started-with-visual-studio-tools-for-unity.md).

## <a name="intellisense-for-unity-messages"></a>IntelliSense для сообщений Unity
Автозавершение кода IntelliSense позволяет легко и просто [реализовать сообщения Unity API](using-visual-studio-tools-for-unity.md#intellisense-for-unity-api-messages), например `OnCollisionEnter`, включая их параметры.

![Диалоговое окно IntelliSense с OnCollisionEnter](../media/vs/intellisense-example.png)

## <a name="superior-debugging"></a>Расширенные возможности отладки
Инструменты Visual Studio для Unity поддерживают надежные функции [отладки](using-visual-studio-tools-for-unity.md#unity-debugging), характерные для Visual Studio:

* Задавайте точки останова, включая условные.
* Оценивайте сложные выражения в окне "Контрольные значения".
* Проверяйте и изменяйте значения переменных и аргументов.
* Детализируйте сложные объекты и структуры данных.

![Остановка в точке останова для проверки переменных](../media/vs/debugging-inspecting.png)

## <a name="integrated-suggestions-for-best-practices-and-performance-insights"></a>Интегрированные предложения для получения рекомендаций и аналитических сведений о производительности
Напишите эффективный код, сочетающий в себе лучшие методики и глубокое понимание проектов Unity Visual Studio.

![Сравнение строк рефакторинга VS с CompareTag](../media/vs/unity-diagnostics.png)

## <a name="codelens-support-for-unity-scripts-and-messages"></a>Поддержка CodeLens для скриптов и сообщений Unity
Функции скриптов и сообщений Unity снабжены указаниями, упрощающими распознавание данных, предоставляемых Unity, и вашего кода.

 ![Новый скрипт, демонстрирующий указания CodeLens для скрипта Unity и сообщения Unity](../media/vs/codelens-support.png)

> [!NOTE]
> Поддержка CodeLens реализована в Visual Studio версии 2019.

## <a name="optimized-view-of-all-your-scripts-to-match-unity"></a>Оптимизированное представление всех скриптов в соответствии с Unity
Обозреватель проектов Unity (UPE) — это альтернативный способ просмотра файлов проекта по сравнению со стандартным обозревателем решений. UPE фильтрует указанные файлы и представляет их в иерархии, соответствующей Unity (**Вид > Обозреватель проектов Unity** в Visual Studio 2019).

![Обозреватель проектов Unity](../media/vs/unity-project-explorer.png)

> [!NOTE]
> Обозреватель проектов Unity доступен в Visual Studio 2019. В Visual Studio для Mac Панель решения имеет аналогичное поведение по умолчанию для проектов Unity. Дополнительные представления не требуются.

* [Начало работы с инструментами Visual Studio для Unity](getting-started-with-visual-studio-tools-for-unity.md)
