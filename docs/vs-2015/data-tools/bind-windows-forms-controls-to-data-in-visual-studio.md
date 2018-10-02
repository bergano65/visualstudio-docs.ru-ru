---
title: Привязка элементов управления Windows Forms к данным в Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
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
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ce8945fd535f92a15d510a56e9bc39fd178317f4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570660"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Привязка элементов управления Windows Forms к данным в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [управляет привязки Windows Forms к данным в Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio).  
  
  
Можно отобразить данные пользователям приложения путем привязки данных в формы Windows Forms. Чтобы создать эти элементы управления с привязкой к данным, можно перетаскивать элементы из **источников данных** на окно конструктора Windows Forms в Visual Studio. В этом разделе описываются некоторые из наиболее распространенных задач, инструменты и классы, связанные с созданием приложений Windows Forms с привязкой к данным.  
  
 ![Операции перетаскивания источника данных](../data-tools/media/raddata-data-source-drag-operation.png "операции перетаскивания raddata источника данных")  
  
 Общие сведения о создании элементов управления с привязкой к данным в Visual Studio см. в разделе [привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Дополнительные сведения о привязке данных в Windows Forms, см. в разделе [привязки данных Windows Forms](http://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa).  
  
## <a name="in-this-section"></a>Содержание раздела  
  
-   [Привязка элементов управления Windows Forms к данным](../data-tools/bind-windows-forms-controls-to-data.md)  
  
-   [Фиксация внутрипроцессных изменений в элементах управления с привязкой к данным до сохранения данных](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)  
  
-   [Создание таблиц подстановки в приложениях Windows Forms](../data-tools/create-lookup-tables-in-windows-forms-applications.md)  
  
-   [Создание формы Windows Forms для поиска данных](../data-tools/create-a-windows-form-to-search-data.md)  
  
-   [Создание пользовательского элемента управления Windows Forms с простой привязкой данных](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)  
  
-   [Создание пользовательского элемента управления Windows Forms со сложной привязкой данных](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)  
  
-   [Создание пользовательского элемента управления Windows Forms с подстановочной привязкой данных](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)  
  
-   [Передача данных между формами](../data-tools/pass-data-between-forms.md)  
  
## <a name="bindingsource-component"></a>BindingSource - компонент  
 Компонент <xref:System.Windows.Forms.BindingSource> служит двум целям. Во-первых он обеспечивает уровень абстракции, при привязке к данным элементы управления в форме. Элементы управления в форме привязаны к <xref:System.Windows.Forms.BindingSource> компонент (вместо привязки к источнику данных).  
  
 Во-вторых он может управлять коллекцией объектов. Добавление типа для <xref:System.Windows.Forms.BindingSource> создает список этого типа.  
  
 Дополнительные сведения о <xref:System.Windows.Forms.BindingSource> компонента, см. в разделе:  
  
-   [Компонент BindingSource](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)  
  
-   [Общие сведения о компоненте BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
-   [Архитектура компонента BindingSource](http://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)  
  
## <a name="bindingnavigator-control"></a>BindingNavigator - элемент управления  
 Этот компонент предоставляет пользовательский интерфейс для перехода по данным, отображаемым в приложении Windows. Дополнительные сведения см. в разделе [Элемент управления BindingNavigator](http://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).  
  
## <a name="datagridview-control"></a>DataGridView - элемент управления  
 Для отображения и редактирования табличных данных с использованием разного рода источников данных, используйте <xref:System.Windows.Forms.DataGridView> элемента управления. Вы можете привязывать данные к <xref:System.Windows.Forms.DataGridView> с помощью <xref:System.Windows.Forms.DataGridView.DataSource%2A> свойство. Дополнительные сведения см. в разделе [Обзор элемента управления DataGridView](http://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488).  
  
## <a name="see-also"></a>См. также  
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

