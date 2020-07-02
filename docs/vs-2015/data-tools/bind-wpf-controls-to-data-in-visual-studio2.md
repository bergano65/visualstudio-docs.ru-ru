---
title: Привязка элементов управления WPF к данным (часть 2) | Документация Майкрософт
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
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06428a633aec41489a8a77655d6ea9442ffffaa0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540092"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Привязка элементов управления WPF к данным в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] помощью окна **Источники данных** можно создавать элементы управления с привязкой к данным. Сначала добавьте источник данных в окно **Источники данных** . Затем перетащите элементы из окна **Источники данных** в**конструктор WPF**.

## <a name="add-a-data-source-to-the-data-sources-window"></a><a name="adding"></a>Добавление источника данных в окно «Источники данных»
 Перед созданием элементов управления с привязкой к данным необходимо сначала добавить источник данных в окно **Источники данных** .

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>Порядок добавления источника данных в окно "Источники данных"

1. В меню **вид** наведите указатель мыши на пункт **другие окна**и выберите пункт **Источники данных**.

2. Выберите команду **Добавить новый источник данных** и выполните **Мастер настройки источника данных**.

3. Выполните одну из следующих задач для создания элементов управления с привязкой к данным.

    - [Создание элемента управления, привязанного к одному полю данных](#simple).

    - [Создание элемента управления, привязанного к нескольким полям данных](#complex).

    - [Создание набора элементов управления, привязанных к нескольким полям данных](#details).

    - [Привязка данных к существующим элементам управления в конструкторе](#existing).

## <a name="create-a-control-that-is-bound-to-a-single-field-of-data"></a><a name="simple"></a>Создание элемента управления, привязанного к одному полю данных
 После добавления источника данных в окно **Источники данных** можно создать новый элемент управления с привязкой к данным, отображающий одно поле данных, например <xref:System.Windows.Controls.ComboBox> или <xref:System.Windows.Controls.TextBox> .

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>Порядок создания элемента управления, который привязан к одному полю данных

1. В окне **Источники данных** разверните элемент, представляющий таблицу или объект. Найдите дочерний элемент, представляющий столбец или свойство, к которым вы хотите выполнить привязку. Визуальный пример см. в разделе [Data Sources Window](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. При необходимости выберите создаваемый элемент управления. Каждый элемент в окне **Источники данных** имеет элемент управления по умолчанию, который создается при перетаскивании элемента в конструктор. Этот элемент управления по умолчанию зависит от базового типа данных элемента.

     Чтобы выбрать другой элемент управления, щелкните стрелку раскрывающегося списка рядом с элементом и выберите нужный элемент управления. Дополнительные сведения см. в разделе [Установка элемента управления, создаваемого при перетаскивании из окна Источники данных](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

3. Перетащите элемент в допустимый контейнер в конструкторе. Дополнительные сведения о допустимых контейнерах см. [в разделе Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]создает новый элемент управления с привязкой к данным и соответствующим образом заголовком <xref:System.Windows.Controls.Label> в контейнере. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]также создает [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] и код для привязки элемента управления к данным. Дополнительные сведения см. [в разделе Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="create-a-control-that-is-bound-to-multiple-fields-of-data"></a><a name="complex"></a>Создание элемента управления, привязанного к нескольким полям данных
 После добавления источника данных в окно **Источники данных** можно создать новый элемент управления с привязкой к данным, отображающий несколько полей данных, таких как <xref:System.Windows.Controls.DataGrid> или <xref:System.Windows.Controls.ListView> .

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>Порядок создания элемента управления, который привязан к нескольким полям данных

1. В окне **Источники данных** выберите элемент, представляющий таблицу или объект. Визуальный пример см. в разделе [Data Sources Window](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. При необходимости выберите создаваемый элемент управления. По умолчанию каждый элемент в окне **Источники данных** , представляющий таблицу или объект данных, имеет значение создать <xref:System.Windows.Controls.DataGrid> (если проект предназначен для .NET Framework 4) или <xref:System.Windows.Controls.ListView> (для более ранних версий .NET Framework).

     Чтобы выбрать другой элемент управления, щелкните стрелку раскрывающегося списка рядом с элементом и выберите нужный элемент управления. Дополнительные сведения см. в разделе [Установка элемента управления, создаваемого при перетаскивании из окна Источники данных](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    > [!NOTE]
    > Если вы не хотите отображать определенный столбец или определенное свойство, разверните этот элемент для отображения его дочерних элементов. Щелкните стрелку раскрывающегося списка рядом со столбцом или свойством, которое не нужно отображать, и выберите пункт **нет**.

3. Перетащите элемент в допустимый контейнер в конструкторе, например <xref:System.Windows.Controls.Grid>. Дополнительные сведения о допустимых контейнерах см. [в разделе Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]создает новый элемент управления с привязкой к данным в контейнере. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]также создает [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] и код для привязки элемента управления к данным. Дополнительные сведения см. [в разделе Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a><a name="details"></a>Создание набора элементов управления, привязанных к нескольким полям данных
 После добавления источника данных в окно **Источники данных** можно привязать таблицу или объект данных к набору элементов управления. Для каждого столбца или свойства в таблице или объекте создается отдельный элемент управления.

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>Порядок создания набора элементов управления, которые привязаны к нескольким полям данных

1. В окне **Источники данных** выберите элемент, представляющий таблицу или объект. Визуальный пример см. в разделе [Data Sources Window](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Щелкните стрелку раскрывающегося списка рядом с элементом и выберите **сведения**.

    > [!NOTE]
    > Если вы не хотите отображать определенный столбец или определенное свойство, разверните этот элемент для отображения его дочерних элементов. Щелкните стрелку раскрывающегося списка рядом со столбцом или свойством, которое не нужно отображать, и выберите пункт **нет**.

3. Перетащите элемент в допустимый контейнер в конструкторе, например <xref:System.Windows.Controls.Grid>. Дополнительные сведения о допустимых контейнерах см. [в разделе Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]создает в контейнере новые элементы управления с привязкой к данным. Каждый элемент управления привязан к другому столбцу или свойству, и каждый элемент управления сопровождается соответствующим <xref:System.Windows.Controls.Label> элементом управления. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]также создает [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] и код для привязки элементов управления к данным. Дополнительные сведения см. [в разделе Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="binddata-to-existing-controls-in-the-designer"></a><a name="existing"></a>Бинддата к существующим элементам управления в конструкторе
 После добавления источника данных в окно **Источники данных** можно добавить привязку данных к существующему элементу управления в конструкторе.

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>Порядок привязки данных к существующему элементу управления в конструкторе.

1. В окне **Источники данных** выполните одну из следующих процедур.

    - Чтобы добавить привязку к данным в существующий элемент управления, который отображает несколько полей данных, например <xref:System.Windows.Controls.DataGrid> или <xref:System.Windows.Controls.ListView>, выберите элемент, представляющий таблицу или объект, которые вы хотите привязать к элементу управления.

    - Чтобы добавить привязку к данным в существующий элемент управления, который отображает одно поле данных, например <xref:System.Windows.Controls.ComboBox> или <xref:System.Windows.Controls.TextBox>, разверните элемент, представляющий таблицу или объект, которые содержат данные, а затем выберите элемент, представляющий данные, которые вы хотите привязать к элементу управления.

2. Перетащите выбранный элемент из окна **Источники данных** на существующий элемент управления в конструкторе. Этот элемент управления должен быть допустимым конечным расположением сброса. Дополнительные сведения см. [в разделе Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]создает [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] и код для привязки элемента управления к данным. Дополнительные сведения см. [в разделе Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

    > [!NOTE]
    > Если элемент управления уже привязан к данным, привязка к данным для него сбрасывается на элемент, который был перетащен на этот элемент управления последним.

## <a name="see-also"></a>См. также
 [Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [Создание таблиц подстановки в приложениях WPF](../data-tools/create-lookup-tables-in-wpf-applications.md) [Отображение связанных данных в приложениях WPF](../data-tools/display-related-data-in-wpf-applications.md) [Привязка элементов управления WPF к набору данных](../data-tools/bind-wpf-controls-to-a-dataset.md) [Привязка](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) элементов управления WPF к DataSet [. Отображение связанных данных в приложении WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
