---
title: Работа с наборами данных в n-уровневых приложениях
description: Научитесь работать с наборами данных в n-уровневых приложениях. N-уровневые приложения для обработки данных — это приложения, ориентированные на данные, разделенные на несколько логических слоев (или уровней).
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 93a221640ff7383b39bfdec73cbaa9659156e33f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858076"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Работа с наборами данных в n-уровневых приложениях

*N-уровневые приложения* для обработки данных — это ориентированные на данные приложения, разделенные на несколько логических слоев (или *уровней*). Другими словами, n-уровневое приложение — это приложение, которое разделено на несколько проектов, при этом уровень доступа к данным, уровень бизнес-логики и уровень представления находятся каждый в своем отдельном проекте. Дополнительные сведения см. в статье [Общие сведения о N-уровневых приложениях данных](../data-tools/n-tier-data-applications-overview.md).

Типизированные наборы данных были усовершенствованы, поэтому адаптеры таблицы и классы наборов данных можно создавать в отдельных проектах. Это дает возможность быстро разделять слои приложения и формировать n-уровневые приложения для обработки данных.

N-уровневая поддержка в типизированных наборах данных позволяет итеративно разрабатывать архитектуру приложения в n-уровневой конструкции. Также устраняется необходимость разделения кода вручную на более одного проекта. Начните разработку уровня данных с помощью **Конструктор наборов данных**. Когда все готово к переводу архитектуры приложения на n-уровневую структуру, задайте свойство **Проект DataSet** набора данных, чтобы сформировать класс набора данных в отдельном проекте.

## <a name="reference"></a>Справочник

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>См. также

- [Обзор многоуровневых приложений для данных](../data-tools/n-tier-data-applications-overview.md)
- [Пошаговое руководство. Создание n-уровневого приложения для данных](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Добавление кода для объектов TableAdapter в n-уровневых приложениях](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Добавление кода для наборов данных в n-уровневых приложениях](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Добавление проверки в n-уровневом наборе данных](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Разделение наборов данных и адаптеров таблиц на разные проекты](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Иерархическое обновление](../data-tools/hierarchical-update.md)
- [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Создание и настройка адаптеров таблиц TableAdapter](../data-tools/create-and-configure-tableadapters.md)
- [N-уровневые и удаленные приложения с LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)
