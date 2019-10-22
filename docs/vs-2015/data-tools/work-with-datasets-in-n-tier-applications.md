---
title: Работа с наборами данных в n-уровневых приложениях | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f7be307ec94b15871da20ace8055fc7121d5d92
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657815"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Работа с наборами данных в n-уровневых приложениях
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N-уровневые приложения для обработки данных * — это приложения, ориентированные на данные, разделенные на несколько логических слоев (или *уровней*). Другими словами, n-уровневое приложение — это приложение, которое разделено на несколько проектов, при этом уровень доступа к данным, уровень бизнес-логики и уровень представления находятся каждый в своем отдельном проекте. Дополнительные сведения см. в статье [Общие сведения о N-уровневых приложениях данных](../data-tools/n-tier-data-applications-overview.md).

 Типизированные наборы данных были усовершенствованы, поэтому адаптеры таблицы и классы наборов данных можно создавать в отдельных проектах. Это дает возможность быстро разделять слои приложения и формировать n-уровневые приложения для обработки данных.

 N-уровневая поддержка в типизированных наборах данных позволяет итеративно разрабатывать архитектуру приложения в n-уровневой конструкции. Также устраняется необходимость разделения кода вручную на более одного проекта. Начните разработку уровня данных с помощью конструктор наборов данных. Когда все готово к переводу архитектуры приложения на n-уровневую структуру, задайте свойство **Проект DataSet** набора данных, чтобы сформировать класс набора данных в отдельном проекте.

## <a name="in-this-section"></a>Содержание
 [Отделение наборов данных и адаптеров таблиц к разным проектам](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md) Описывает, как переместить созданный класс набора данных из проекта, содержащего созданные классы TableAdapter и в новый проект.

 [Добавление кода для адаптеров таблиц в n-уровневые приложения](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md) Описывает, как создать разделяемый класс, в котором можно добавить код для n-уровневого TableAdapter.

 [Добавление кода в наборы данных в n-уровневых приложениях](../data-tools/add-code-to-datasets-in-n-tier-applications.md) Описывает, как создать разделяемый класс, в котором можно добавить код для n-уровневого набора данных.

 [Добавление проверки в n-уровневый набор данных](../data-tools/add-validation-to-an-n-tier-dataset.md) Описывает, куда добавить код для выполнения проверки изменений данных.

 [Пошаговое руководство. Создание N-уровневого приложения для данных](../data-tools/walkthrough-creating-an-n-tier-data-application.md) Содержит пошаговые инструкции по созданию типизированного набора данных и разделению TableAdapter и кода набора данных на несколько проектов.

 [Пошаговое руководство. Добавление проверки в N-уровневое приложение для данных](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265) Содержит пошаговые инструкции по добавлению проверки в приложение, созданное в пошаговом руководстве по многоуровневому приложению для данных.

## <a name="reference"></a>Справочник
 <xref:System.Data.DataSet>

 <xref:System.Data.TypedTableBase%601>

## <a name="related-sections"></a>Связанные разделы

- [Общие сведения о N-уровневых приложениях для работы с данными](../data-tools/n-tier-data-applications-overview.md)
- [Иерархическое обновление](../data-tools/hierarchical-update.md)
- [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [N-уровневые и удаленные приложения и LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)