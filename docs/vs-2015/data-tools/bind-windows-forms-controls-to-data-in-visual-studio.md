---
title: Привязка элементов управления Windows Forms к данным
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a03f4df57b216fa68e5ac24df80b67917aa3e3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672988"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Привязка элементов управления Windows Forms к данным в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете отображать данные для пользователей приложения, привязывая данные к Windows Forms. Чтобы создать эти элементы управления с привязкой к данным, можно перетащить элементы из окна **Источники данных** на конструктор Windows Forms в Visual Studio. В этом разделе описываются некоторые из наиболее распространенных задач, средств и классов, участвующих в создании Windows Forms приложений с привязкой к данным.

 ![Операция перетаскивания источника данных](../data-tools/media/raddata-data-source-drag-operation.png "операция перетаскивания источника данных раддата")

 Общие сведения о создании элементов управления с привязкой к данным в Visual Studio см. [в разделе Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Дополнительные сведения о привязке данных в Windows Forms см. в разделе [Windows Forms привязка данных](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa).

## <a name="in-this-section"></a>В этом разделе

- [Привязка элементов управления Windows Forms к данным](../data-tools/bind-windows-forms-controls-to-data.md)

- [Фиксация внутрипроцессных изменений в элементах управления с привязкой к данным до сохранения данных](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)

- [Создание таблиц подстановки в приложениях Windows Forms](../data-tools/create-lookup-tables-in-windows-forms-applications.md)

- [Создание формы Windows Forms для поиска данных](../data-tools/create-a-windows-form-to-search-data.md)

- [Создание пользовательского элемента управления Windows Forms с простой привязкой данных](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)

- [Создание пользовательского элемента управления Windows Forms со сложной привязкой данных](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)

- [Создание пользовательского элемента управления Windows Forms с подстановочной привязкой данных](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)

- [Передача данных между формами](../data-tools/pass-data-between-forms.md)

## <a name="bindingsource-component"></a>BindingSource - компонент
 Компонент <xref:System.Windows.Forms.BindingSource> служит двум целям. Во-первых, он предоставляет уровень абстракции при привязке элементов управления в форме к данным. Элементы управления формы привязаны к <xref:System.Windows.Forms.BindingSource> компоненту (вместо привязки непосредственно к источнику данных).

 Во-вторых, он может управлять коллекцией объектов. Добавление типа в <xref:System.Windows.Forms.BindingSource> создает список этого типа.

 Дополнительные сведения о <xref:System.Windows.Forms.BindingSource> компоненте см. в следующих статьях:

- [Компонент BindingSource](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)

- [Общие сведения о компоненте BindingSource](https://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)

- [Архитектура компонента BindingSource](https://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)

## <a name="bindingnavigator-control"></a>BindingNavigator - элемент управления
 Этот компонент предоставляет пользовательский интерфейс для навигации по данным, отображаемым приложением Windows. Дополнительные сведения см. в разделе [Элемент управления BindingNavigator](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

## <a name="datagridview-control"></a>DataGridView - элемент управления
 Чтобы отобразить и изменить табличные данные из различных типов источников данных, используйте <xref:System.Windows.Forms.DataGridView> элемент управления. Вы можете привязать данные к, <xref:System.Windows.Forms.DataGridView> используя <xref:System.Windows.Forms.DataGridView.DataSource%2A> свойство. Дополнительные сведения см. в разделе [Общие сведения об элементе управления DataGridView](https://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488).

## <a name="see-also"></a>См. также:
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
