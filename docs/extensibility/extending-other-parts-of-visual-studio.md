---
title: Расширение других частей Visual Studio | Документация Майкрософт
description: Узнайте о частях пользовательского интерфейса Visual Studio, которые можно расширить. Можно создать пакет VSPackage, записать его в журнал действий и расширить область элементов и строку состояния.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces
ms.assetid: 27d2f1e1-2503-4aca-9cfc-707abd07ccf0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e21c5b8a3570b4da0cb0286d3c0d6d7c84c2f704
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895847"
---
# <a name="extend-other-parts-of-visual-studio"></a>Расширение других частей Visual Studio

Существует множество дополнительных частей пользовательского интерфейса Visual Studio, которые можно расширить. Здесь мы покажем всего несколько.

## <a name="create-a-vspackage"></a>Создание VSPackage

Основными стандартными блоками расширения Visual Studio являются пакеты VSPackage.  Узнайте, как добавить пакет VSPackage: [Создание расширения с помощью VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

## <a name="extend-the-toolbox"></a>Расширение области элементов

Узнайте, как добавлять новые элементы управления и другие элементы на панель элементов и как использовать функциональные возможности панели элементов.

- [Создание элемента управления панели элементов WPF](../extensibility/creating-a-wpf-toolbox-control.md)

- [Создание Windows Forms элемента управления панели элементов](../extensibility/creating-a-windows-forms-toolbox-control.md)

## <a name="extend-the-status-bar"></a>Расширение строки состояния

Узнайте, как выполнять чтение и запись в строке состояния и на индикаторе выполнения, а также как предоставлять анимацию и другой пользовательский интерфейс: [расширять строку состояния](../extensibility/extending-the-status-bar.md).

::: moniker range="vs-2017"

## <a name="create-custom-start-pages"></a>Создание настраиваемых начальных страниц

Узнайте, как создать собственную начальную страницу, с нуля или с помощью загружаемого образца начальной страницы: [Создание настраиваемой начальной страницы](../extensibility/creating-a-custom-start-page.md).

::: moniker-end

## <a name="write-to-the-activity-log"></a>Запись в журнал действий

Сведения о записи в журнал действий: [как использовать журнал действий](../extensibility/how-to-use-the-activity-log.md).
