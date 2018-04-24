---
title: Фиксация внутрипроцессных для элементов управления с привязкой к данным до сохранения данных
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- commiting edited records
- data-bound controls, in-process edits
- DataBinding class, commiting edited records
- hierarchical update, commiting edited records
- BindingSource class, commiting edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a0811ec9338bfb84235679a68d32169435eb57a5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Фиксация внутрипроцессных для элементов управления с привязкой к данным до сохранения данных

При изменении значения в элементах управления с привязкой к данным, пользователь должен перейти с текущей записи для фиксации обновленного значения в источнике данных, к которому привязан элемент управления. При перетаскивании элементов из [окно "Источники данных"](add-new-data-sources.md) на форму, первый элемент, перетаскиваемая приводит к возникновению ошибки кода в **Сохранить** нажатия кнопки <xref:System.Windows.Forms.BindingNavigator>. Этот код вызывает <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод <xref:System.Windows.Forms.BindingSource>. Таким образом, вызов <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод создается только для первого <xref:System.Windows.Forms.BindingSource> , добавленного в форму.

<xref:System.Windows.Forms.BindingSource.EndEdit%2A> Вызов фиксирует все изменения, находящиеся в процессе во всех элементах управления с привязкой к данным, изменяемых в настоящее время. Таким образом, если элемент управления с привязкой к данным по-прежнему имеет фокус и вы нажимаете **Сохранить** кнопку все ожидающие правки в этом элементе управления фиксируются до фактического сохранения ( `TableAdapterManager.UpdateAll` метода).

Можно настроить приложение на автоматическую фиксацию изменений, даже если пользователь пытается сохранить данные без фиксации изменений в процессе сохранения процесса.

> [!NOTE]
> Конструктор добавляет `BindingSource.EndEdit` код только для первого элемента, помещенной на форму. Таким образом, вам необходимо добавить строку кода для вызова <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод для каждого <xref:System.Windows.Forms.BindingSource> в форме. Можно вручную добавить строку кода для вызова <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод для каждого <xref:System.Windows.Forms.BindingSource>. Кроме того, можно добавить `EndEditOnAllBindingSources` метод в форму и вызовите ее, прежде чем выполнить сохранение.

В следующем коде используется [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) запроса для перечисления всех <xref:System.Windows.Forms.BindingSource> компоненты и вызова <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод для каждого <xref:System.Windows.Forms.BindingSource> на форме.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Для вызова EndEdit для всех компонентов BindingSource на форме

1.  Добавьте следующий код в форму, содержащую <xref:System.Windows.Forms.BindingSource> компонентов.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2.  Добавьте следующую строку кода непосредственно перед любыми вызовами сохранения данных формы ( `TableAdapterManager.UpdateAll()` метод):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>См. также

- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Иерархическое обновление](../data-tools/hierarchical-update.md)