---
title: Фиксировать в процессе изменения в элементах управления с привязкой к данным перед сохранением данных | Документация Майкрософт
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
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3867b91a8b417b5670514b66aaf93fdab4e9618c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662452"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Фиксация внутрипроцессных изменений в элементах управления с привязкой к данным до сохранения данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При изменении значений в элементах управления с привязкой к данным пользователи должны переходить от текущей записи для фиксации обновленного значения в базовом источнике данных, к которому привязан элемент управления. При перетаскивании элементов из [окна «Источники данных](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) » на форму первый элемент, который удаляется, создает код для события нажатия кнопки « **сохранить** » <xref:System.Windows.Forms.BindingNavigator>. Этот код вызывает метод <xref:System.Windows.Forms.BindingSource.EndEdit%2A> <xref:System.Windows.Forms.BindingSource>. Поэтому вызов метода <xref:System.Windows.Forms.BindingSource.EndEdit%2A> создается только для первого <xref:System.Windows.Forms.BindingSource>, добавленного в форму.

 Вызов <xref:System.Windows.Forms.BindingSource.EndEdit%2A> фиксирует все актуальные изменения для всех редактируемых в настоящее время элементов управления с привязкой к данным. Таким образом, если элемент управления с привязкой к данным все еще находится в фокусе и вы нажимаете кнопку **Сохранить**, все ожидающие правки в этом элементе управления фиксируются до фактического сохранения (метод `TableAdapterManager.UpdateAll`).

 Можно настроить приложение на автоматическую фиксацию изменений, даже если пользователь пытается сохранить данные без фиксации изменений в ходе процесса сохранения.

> [!NOTE]
> Конструктор добавляет код `BindingSource.EndEdit` только для первого элемента, помещенного в форму. Поэтому необходимо добавить строку кода для вызова метода <xref:System.Windows.Forms.BindingSource.EndEdit%2A> для каждого <xref:System.Windows.Forms.BindingSource> в форме. Можно вручную добавить строку кода для вызова метода <xref:System.Windows.Forms.BindingSource.EndEdit%2A> для каждой <xref:System.Windows.Forms.BindingSource>. Кроме того, можно добавить метод `EndEditOnAllBindingSources` в форму и вызвать его перед выполнением сохранения.

 В следующем коде используется запрос [LINQ (запрос языка)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) для итерации всех <xref:System.Windows.Forms.BindingSource> компонентов и вызова метода <xref:System.Windows.Forms.BindingSource.EndEdit%2A> для каждого <xref:System.Windows.Forms.BindingSource> в форме.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Вызов EndEdit для всех компонентов BindingSource в форме

1. Добавьте следующий код в форму, содержащую компоненты <xref:System.Windows.Forms.BindingSource>.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]

2. Добавьте следующую строку кода непосредственно перед вызовами, чтобы сохранить данные формы (метод `TableAdapterManager.UpdateAll()`):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]

## <a name="see-also"></a>См. также раздел
 [Привязка элементов управления Windows Forms к данным в](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [иерархическом обновлении](../data-tools/hierarchical-update.md) Visual Studio
