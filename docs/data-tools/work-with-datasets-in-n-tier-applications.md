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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c7532bed6a7d43c24d698870723d2265fc2b176f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585929"
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
- [Добавление кода для объектов TableAdapter в многоуровневых приложениях](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Добавление кода для наборов данных в многоуровневых приложениях](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Добавление проверки в n-уровневый набор данных](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Разделение наборов данных и адаптеров таблиц на разные проекты](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Иерархическое обновление](../data-tools/hierarchical-update.md)
- [Инструменты набора данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Создание и настройка адаптеров таблиц](../data-tools/create-and-configure-tableadapters.md)
- [N-уровневые и удаленные приложения с LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)
