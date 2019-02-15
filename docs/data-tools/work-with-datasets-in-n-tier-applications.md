---
title: Работа с наборами данных в n-уровневых приложениях
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c6da3f51a249aaf52cf3f20b90f3add6ceeb7aa1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55936555"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Работа с наборами данных в n-уровневых приложениях

*N-уровневые приложения для обработки данных* — это нацеленные на обработку данных приложения, которые разделены на несколько логических слоев (или *уровней*). Другими словами, n-уровневое приложение — это приложение, которое разделено на несколько проектов, при этом уровень доступа к данным, уровень бизнес-логики и уровень представления находятся каждый в своем отдельном проекте. Дополнительные сведения см. в разделе [Общие сведения о приложениях данных N-уровневых](../data-tools/n-tier-data-applications-overview.md).

Типизированные наборы данных были усовершенствованы, поэтому адаптеры таблицы и классы наборов данных можно создавать в отдельных проектах. Это дает возможность быстро разделять слои приложения и формировать n-уровневые приложения для обработки данных.

Поддержка N-уровневой в типизированных наборах данных позволяет применять последовательную разработку архитектуры приложения для n уровневой структуры. Он также устраняет необходимость в ручном разделении кода в более одного проекта. Начните проектировать уровень данных с помощью **конструктор наборов данных**. Когда все готово к переводу архитектуры приложения на n-уровневую структуру, задайте свойство **Проект DataSet** набора данных, чтобы сформировать класс набора данных в отдельном проекте.

## <a name="reference"></a>Ссылка

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>См. также

- [Общие сведения об n-уровневых приложениях](../data-tools/n-tier-data-applications-overview.md)
- [Пошаговое руководство. Создание n-уровневого приложения для работы с данными](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Добавление кода для объектов TableAdapter в многоуровневых приложениях](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Добавление кода для наборов данных в многоуровневых приложениях](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Добавление проверки в N-уровневом наборе данных](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Разделение наборов данных и адаптеров таблиц на разные проекты](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Иерархическое обновление](../data-tools/hierarchical-update.md)
- [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Создание и настройка адаптеров таблиц](../data-tools/create-and-configure-tableadapters.md)
- [N-уровневые и удаленные приложения с LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)