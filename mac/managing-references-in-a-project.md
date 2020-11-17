---
title: Управление ссылками в проекте
description: В этой статье описывается управление ссылками в проекте в Visual Studio для Mac
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.topic: overview
ms.openlocfilehash: 41d49fe6b23818f3cb9de8dec72462d4b2029bb6
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493521"
---
# <a name="managing-references-in-a-project"></a>Управление ссылками в проекте

Visual Studio для Mac предоставляет два средства для добавления дополнительных ссылок в проект:

![Ссылки проекта](media/projects-and-solutions-image10.png)

Эти особые значения приведены ниже.

* Ссылки
* Пакеты NuGet (добавляются через папку "Пакеты")

Кроме того, в любой проект можно добавить веб-ссылки и собственные ссылки.

## <a name="assembly-references"></a>Ссылки на сборки

Каждая платформа в Xamarin содержит более десяти различных сборок. Не все эти пакеты сборки указываются в ссылках вашего проекта по умолчанию.

Чтобы изменить пакеты, на которые указывают ссылки в проекте, используйте диалоговое окно **Изменить ссылки**, которое отображается при двойном щелчке папки ссылок или выборе пункта **Изменить ссылки** в ее контекстном меню.

![Диалоговое окно "Ссылки на сборки"](media/projects-and-solutions-image11.png)

Сведения о сборках, доступных для каждой платформы Xamarin, см. в руководстве [Доступные сборки](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/).

## <a name="nuget"></a>NuGet

NuGet — это наиболее популярный диспетчер пакетов для разработки .NET. Поддержка NuGet в Visual Studio для Mac позволяет искать пакеты, которые требуется добавить в проект.

Для этого щелкните папку **Пакеты** в окне решения правой кнопкой мыши и выберите пункт "Добавить пакеты".

Сведения об использовании пакета NuGet см. в пошаговом руководстве [Включение пакета NuGet в проект](nuget-walkthrough.md).

## <a name="see-also"></a>См. также

- [Управление ссылками (Visual Studio в Windows)](/visualstudio/ide/managing-references-in-a-project)
- [Добавление ссылок с использованием NuGet или расширения SDK (Visual Studio в Windows)](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)