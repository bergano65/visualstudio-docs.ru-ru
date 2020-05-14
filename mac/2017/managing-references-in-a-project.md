---
title: Управление ссылками в проекте
description: В этой статье описывается управление ссылками в проекте в Visual Studio для Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: f9925954083c7fe64ad29c7cfed618a84d7a6386
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984865"
---
# <a name="managing-references-in-a-project"></a>Управление ссылками в проекте

Visual Studio для Mac предоставляет два средства для добавления дополнительных ссылок в проект:

![Ссылки на проект](media/projects-and-solutions-image10.png)

а именно:

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

Для этого щелкните папку **Пакет** на панели решения правой кнопкой мыши и выберите пункт "Добавить пакеты".

Сведения об использовании пакета NuGet см. в пошаговом руководстве [Включение пакета NuGet в проект](nuget-walkthrough.md).

## <a name="see-also"></a>См. также раздел

- [Управление ссылками (Visual Studio в Windows)](/visualstudio/ide/managing-references-in-a-project)
- [Добавление ссылок с использованием NuGet или расширения SDK (Visual Studio в Windows)](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)