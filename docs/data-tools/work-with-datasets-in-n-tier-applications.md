---
title: "Работа с наборами данных в n уровневых приложениях | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 2274ac9bcfd3ba7c87364f5c4c79cd155844fe73
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Работа с наборами данных в n уровневых приложениях
*Многоуровневые приложения* , ориентированных на данные приложений, разделенные на несколько логических слоев (или *уровни*). Другими словами, n-уровневое приложение — это приложение, которое разделено на несколько проектов, при этом уровень доступа к данным, уровень бизнес-логики и уровень представления находятся каждый в своем отдельном проекте. Дополнительные сведения см. в разделе [Общие сведения о приложениях данных N-уровневые](../data-tools/n-tier-data-applications-overview.md).  
  
Типизированные наборы данных были усовершенствованы, поэтому адаптеры таблицы и классы наборов данных можно создавать в отдельных проектах. Это дает возможность быстро разделять слои приложения и формировать n-уровневые приложения для обработки данных.  
  
Поддержка N-уровневой в типизированных наборах данных позволяет применять последовательную разработку архитектуры приложения до n уровневой структуры. Он также устраняет необходимость в ручном разделении кода на несколько проектов. Начните с проектирования уровня данных с помощью **конструктора наборов данных**. Когда вы будете готовы к переводу архитектуры приложения до n уровневой структуры, задайте **DataSet проекта** свойства набора данных для создания класса набора данных в отдельном проекте.  
  
## <a name="reference"></a>Ссылка  
<xref:System.Data.DataSet>  
<xref:System.Data.TypedTableBase%601>  
  
## <a name="see-also"></a>См. также
[Общие сведения о N-уровневых приложениях для работы с данными](../data-tools/n-tier-data-applications-overview.md)  
[Пошаговое руководство. Создание многоуровневого приложения для работы с данными](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
[Добавление кода для объектов TableAdapter в многоуровневых приложениях](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
[Добавление кода для наборов данных в многоуровневых приложениях](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
[Добавление проверки в N-уровневом наборе данных](../data-tools/add-validation-to-an-n-tier-dataset.md)  
[Разделение наборов данных и адаптеров таблиц на разные проекты](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
[Иерархическое обновление](../data-tools/hierarchical-update.md)  
[Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
[Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
[Создайте и настройте адаптеры таблиц TableAdapter](../data-tools/create-and-configure-tableadapters.md)  
[N-уровневые и удаленные приложения и LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)