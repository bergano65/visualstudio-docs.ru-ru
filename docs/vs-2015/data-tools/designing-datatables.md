---
title: Разработка объектов DataTable | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VSDesigner.DataSource.DesignTable
- Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner
- vbdata.Microsoft.VSDesigner.DataSource.DesignTable
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- tables [Visual Studio]
- data [Visual Studio], designing DataTables
- DataTable objects
ms.assetid: 17014125-ab28-45ec-8789-01b6fc9a8e6a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f952fbcf6da0185e4f9c1bd6a76b7d15d7f772a9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570622"
---
# <a name="designing-datatables"></a>Разработка объектов DataTable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] предоставляет средства разработки для создания и редактирования таблиц данных (**DataTable**). Общие сведения о том, что **DataTable** см. в разделе [DataTables](http://msdn.microsoft.com/library/52ff0e32-3e5a-41de-9a3b-7b04ea52b83e).  
  
 В следующих разделах объясняется, как создать таблицу данных, добавить их к типизированным наборам данных с помощью **конструктор наборов данных**, а также создавать и изменять столбцы данных (**DataColumn**), которые определяют их.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Практическое руководство. Создание таблиц данных](../data-tools/how-to-create-data-tables.md)  
 Пошаговые инструкции для создания нового <xref:System.Data.DataTable> с **конструктор наборов данных**.  
  
 [Практическое: Добавление столбцов в объект DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)  
 Пошаговые инструкции для создания нового <xref:System.Data.DataColumn> в существующем <xref:System.Data.DataTable>.  
  
 [Пошаговое руководство. Создание объекта DataTable с помощью конструктора наборов данных](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)  
 Содержит пошаговые инструкции по созданию <xref:System.Data.DataTable> и определение <xref:System.Data.DataColumn>, составляющих его структуру.  
  
## <a name="reference"></a>Ссылка  
 <xref:System.Data.DataSet>  
 Представляет кэш данных в памяти.  
  
 <xref:System.Data.DataTable>  
 Представляет одну таблицу данных в памяти.  
  
 <xref:System.Data.DataColumn>  
 Представляет схему столбца в <xref:System.Data.DataTable>.  
  
 <xref:System.Data.DataRelation>  
 Представляет отношение "родительский-дочерний объект" между двумя объектами <xref:System.Data.DataTable>.  
  
## <a name="related-sections"></a>Связанные разделы  
 [DataTables](http://msdn.microsoft.com/library/52ff0e32-3e5a-41de-9a3b-7b04ea52b83e)  
 Описывается, как создавать и настраивать `DataTable` объектов.  
  
 [Адаптеры таблиц](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)  
 Ссылки на разделы, в которых объясняется, как создание и изменение объектов TableAdapter с помощью средств разработки.  
  
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)  
 Ссылки на разделы с описанием различных способов подключения к данным в Visual Studio.  
  
 [Подготовка приложения для получения данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)  
 Ссылки на разделы, описывающие наборы данных, как создать новые наборы данных и как создавать и изменять отдельные объекты, они состоят.  
  
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)  
 Ссылки на разделы, объясняющие, как выполнять запросы и хранимые процедуры и загрузки данных в наборы данных.  
  
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
 Ссылки на разделы, в которых объясняется, как отображать данные в формах Windows Forms с помощью элементов управления с привязкой к данным.  
  
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)  
 Содержит ссылки на разделы, в которых объясняется работа с данными в наборе данных.  
  
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 Ссылки на разделы, объясняющие, куда следует поместить код для проверки данных.  
  
 [Сохранение данных](../data-tools/saving-data.md)  
 Ссылки на разделы с объяснением процедуры отправки обновленных данных из приложения к базе данных.