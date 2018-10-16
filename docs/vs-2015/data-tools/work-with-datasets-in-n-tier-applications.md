---
title: Работа с наборами данных в n уровневых приложениях | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d05204edfd7c3cd5daecad3a1cb21ba5ba7e60d8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205976"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Работа с наборами данных в n-уровневых приложениях
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Данные N-уровневых приложений *, ориентированных на данные приложений, разделенные на несколько логических слоев (или *уровни*). Другими словами, n-уровневое приложение — это приложение, которое разделено на несколько проектов, при этом уровень доступа к данным, уровень бизнес-логики и уровень представления находятся каждый в своем отдельном проекте. Дополнительные сведения см. в разделе [Общие сведения о приложениях данных N-уровневых](../data-tools/n-tier-data-applications-overview.md).  
  
 Типизированные наборы данных были усовершенствованы, поэтому адаптеры таблицы и классы наборов данных можно создавать в отдельных проектах. Это дает возможность быстро разделять слои приложения и формировать n-уровневые приложения для обработки данных.  
  
 Поддержка N-уровневой в типизированных наборах данных позволяет применять последовательную разработку архитектуры приложения для n уровневой структуры. Он также устраняет необходимость в ручном разделении кода в более одного проекта. Начните проектировать уровень данных с помощью [Создание и изменение типизированных наборов DataSet](../data-tools/creating-and-editing-typed-datasets.md). Когда вы будете готовы к переводу архитектуры приложения для n уровневую структуру, задайте **проект DataSet** свойства набора данных для создания класса набора данных в отдельном проекте.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Разделение наборов данных и адаптеров таблиц на разные проекты](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 Описывает, как переместить созданный класс набора данных из проекта, содержащего созданные классы адаптера таблицы, и поместить в новый проект.  
  
 [Добавление кода для объектов TableAdapter в многоуровневых приложениях](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 Описывает, как создать разделяемый класс, в котором код можно добавлять для n-уровневого адаптера таблицы.  
  
 [Добавление кода для наборов данных в многоуровневых приложениях](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 Описывает, как создать разделяемый класс, в котором код можно добавлять для n-уровневого набора данных.  
  
 [Добавление проверки в N-уровневом наборе данных](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 Описывает, куда нужно добавить код для выполнения проверки изменения данных.  
  
 [Пошаговое руководство. Создание многоуровневого приложения для работы с данными](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 Содержит пошаговые инструкции по созданию типизированного набора данных и разделения кода адаптера таблицы и набора данных на несколько проектов.  
  
 [Пошаговое руководство: Добавление проверки в N-уровневое приложение](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)  
 Содержит пошаговые инструкции по добавлению проверки в приложение, который был создан в пошаговом руководстве данных n уровневого приложения.  
  
## <a name="reference"></a>Ссылка  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## <a name="related-sections"></a>Связанные разделы  
 [Общие сведения о N-уровневых приложениях для работы с данными](../data-tools/n-tier-data-applications-overview.md)  
  
 [Иерархическое обновление](../data-tools/hierarchical-update.md)  
  
 [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
 [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
  
 [Общие сведения об адаптере таблиц](../data-tools/tableadapter-overview.md)  
  
 [N-уровневые и удаленные приложения и LINQ to SQL](http://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)

