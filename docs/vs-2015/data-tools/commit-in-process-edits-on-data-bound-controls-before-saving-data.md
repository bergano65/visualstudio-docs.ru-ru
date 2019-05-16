---
title: Фиксация внутрипроцессных изменений в элементах управления с привязкой к данным до сохранения данных | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2def3f3512e7a6ebc2e084f0bca4d6b1707ecd04
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699482"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Фиксация внутрипроцессных изменений в элементах управления с привязкой к данным до сохранения данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При изменении значения в элементах управления с привязкой к данным, пользователь должен перейти зафиксировать обновленное значение в базовый источник данных, который элемент управления привязывается к текущей записи. При перетаскивании элементов из [окна "Источники данных"](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) в форму, первый элемент, перетаскиваемая создает код в **Сохранить** события нажатия кнопки <xref:System.Windows.Forms.BindingNavigator>. Этот код вызывает <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод <xref:System.Windows.Forms.BindingSource>. Таким образом, вызов <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод создается только для первого <xref:System.Windows.Forms.BindingSource> , добавляется в форму.  
  
 Вызов <xref:System.Windows.Forms.BindingSource.EndEdit%2A> фиксирует все актуальные изменения для всех редактируемых в настоящее время элементов управления с привязкой к данным. Таким образом, если элемент управления с привязкой к данным все еще находится в фокусе и вы нажимаете кнопку **Сохранить**, все ожидающие правки в этом элементе управления фиксируются до фактического сохранения (метод `TableAdapterManager.UpdateAll`).  
  
 Можно настроить приложение на автоматическую фиксацию изменений, даже если пользователь пытается сохранить данные без фиксации изменений в процессе сохранения процесса.  
  
> [!NOTE]
> Конструктор добавляет `BindingSource.EndEdit` код только для первого элемента, помещенной на форму. Таким образом, необходимо добавить строку кода для вызова <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод для каждого <xref:System.Windows.Forms.BindingSource> в форме. Можно вручную добавить строку кода для вызова <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод для каждого <xref:System.Windows.Forms.BindingSource>. Кроме того, можно добавить `EndEditOnAllBindingSources` метод в форму и вызовите его перед выполнением сохранения.  
  
 В следующем коде используется [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) запрос, чтобы выполнять итерации по всем <xref:System.Windows.Forms.BindingSource> компоненты и вызов <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод для каждого <xref:System.Windows.Forms.BindingSource> в форме.  
  
## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Для вызова EndEdit для всех компонентов BindingSource в форме  
  
1. Добавьте следующий код в форму, которая содержит <xref:System.Windows.Forms.BindingSource> компонентов.  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]  
  
2. Добавьте следующую строку кода непосредственно перед любыми вызовами, чтобы сохранить данные формы ( `TableAdapterManager.UpdateAll()` метод):  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>См. также  
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Иерархическое обновление](../data-tools/hierarchical-update.md)
