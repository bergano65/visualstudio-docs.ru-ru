---
title: Фиксация в процессе изменений элементов управления с привязкой к данным перед сохранением
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 129f8e03ca982dc1e028dc23a9e342b5793e39cf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648678"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Фиксация внутрипроцессных изменений в элементах управления с привязкой к данным до сохранения данных

При изменении значений в элементах управления с привязкой к данным пользователи должны переходить от текущей записи для фиксации обновленного значения в базовом источнике данных, к которому привязан элемент управления. При перетаскивании элементов из [окна «Источники данных](add-new-data-sources.md) » на форму первый элемент, который удаляется, создает код для события нажатия кнопки « **сохранить** » <xref:System.Windows.Forms.BindingNavigator>. Этот код вызывает метод <xref:System.Windows.Forms.BindingSource.EndEdit%2A> <xref:System.Windows.Forms.BindingSource>. Поэтому вызов метода <xref:System.Windows.Forms.BindingSource.EndEdit%2A> создается только для первого <xref:System.Windows.Forms.BindingSource>, добавленного в форму.

Вызов <xref:System.Windows.Forms.BindingSource.EndEdit%2A> фиксирует все актуальные изменения для всех редактируемых в настоящее время элементов управления с привязкой к данным. Таким образом, если элемент управления с привязкой к данным все еще находится в фокусе и вы нажимаете кнопку **Сохранить**, все ожидающие правки в этом элементе управления фиксируются до фактического сохранения (метод `TableAdapterManager.UpdateAll`).

Можно настроить приложение на автоматическую фиксацию изменений, даже если пользователь пытается сохранить данные без фиксации изменений в ходе процесса сохранения.

> [!NOTE]
> Конструктор добавляет код `BindingSource.EndEdit` только для первого элемента, помещенного в форму. Поэтому необходимо добавить строку кода для вызова метода <xref:System.Windows.Forms.BindingSource.EndEdit%2A> для каждого <xref:System.Windows.Forms.BindingSource> в форме. Можно вручную добавить строку кода для вызова метода <xref:System.Windows.Forms.BindingSource.EndEdit%2A> для каждой <xref:System.Windows.Forms.BindingSource>. Кроме того, можно добавить метод `EndEditOnAllBindingSources` в форму и вызвать его перед выполнением сохранения.

В следующем коде используется запрос [LINQ (запрос языка)](/dotnet/csharp/linq/) для итерации всех <xref:System.Windows.Forms.BindingSource> компонентов и вызова метода <xref:System.Windows.Forms.BindingSource.EndEdit%2A> для каждого <xref:System.Windows.Forms.BindingSource> в форме.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Вызов EndEdit для всех компонентов BindingSource в форме

1. Добавьте следующий код в форму, содержащую компоненты <xref:System.Windows.Forms.BindingSource>.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2. Добавьте следующую строку кода непосредственно перед вызовами, чтобы сохранить данные формы (метод `TableAdapterManager.UpdateAll()`):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>См. также

- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Иерархическое обновление](../data-tools/hierarchical-update.md)