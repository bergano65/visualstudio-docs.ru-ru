---
title: Фиксация внутрипроцессных изменений в элементах управления с привязкой к данным до сохранения данных
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f771fec52024fb7d1e4c000d374f08929d453917
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112651"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Фиксация внутрипроцессных изменений в элементах управления с привязкой к данным до сохранения данных

При изменении значения в элементах управления с привязкой к данным, пользователь должен перейти зафиксировать обновленное значение в базовый источник данных, который элемент управления привязывается к текущей записи. При перетаскивании элементов из [окна "Источники данных"](add-new-data-sources.md) в форму, первый элемент, перетаскиваемая создает код в **Сохранить** события нажатия кнопки <xref:System.Windows.Forms.BindingNavigator>. Этот код вызывает <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод <xref:System.Windows.Forms.BindingSource>. Таким образом, вызов <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод создается только для первого <xref:System.Windows.Forms.BindingSource> , добавляется в форму.

Вызов <xref:System.Windows.Forms.BindingSource.EndEdit%2A> фиксирует все актуальные изменения для всех редактируемых в настоящее время элементов управления с привязкой к данным. Таким образом, если элемент управления с привязкой к данным все еще находится в фокусе и вы нажимаете кнопку **Сохранить**, все ожидающие правки в этом элементе управления фиксируются до фактического сохранения (метод `TableAdapterManager.UpdateAll`).

Можно настроить приложение на автоматическую фиксацию изменений, даже если пользователь пытается сохранить данные без фиксации изменений в процессе сохранения процесса.

> [!NOTE]
> Конструктор добавляет `BindingSource.EndEdit` код только для первого элемента, помещенной на форму. Таким образом, необходимо добавить строку кода для вызова <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод для каждого <xref:System.Windows.Forms.BindingSource> в форме. Можно вручную добавить строку кода для вызова <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод для каждого <xref:System.Windows.Forms.BindingSource>. Кроме того, можно добавить `EndEditOnAllBindingSources` метод в форму и вызовите его перед выполнением сохранения.

В следующем коде используется [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) запрос, чтобы выполнять итерации по всем <xref:System.Windows.Forms.BindingSource> компоненты и вызов <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод для каждого <xref:System.Windows.Forms.BindingSource> в форме.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Для вызова EndEdit для всех компонентов BindingSource в форме

1. Добавьте следующий код в форму, которая содержит <xref:System.Windows.Forms.BindingSource> компонентов.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2. Добавьте следующую строку кода непосредственно перед любыми вызовами, чтобы сохранить данные формы ( `TableAdapterManager.UpdateAll()` метод):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>См. также

- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Иерархическое обновление](../data-tools/hierarchical-update.md)