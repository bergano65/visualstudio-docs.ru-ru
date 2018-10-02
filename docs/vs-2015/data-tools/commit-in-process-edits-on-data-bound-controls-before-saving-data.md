---
title: Фиксация внутрипроцессных изменений в элементах управления с привязкой к данным до сохранения данных | Документация Майкрософт
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
- commiting edited records
- data-bound controls, in-process edits
- DataBinding class, commiting edited records
- hierarchical update, commiting edited records
- BindingSource class, commiting edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd56f9acfce7933d0bc89e7e86eb8083b9b1f867
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560924"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Фиксация внутрипроцессных изменений в элементах управления с привязкой к данным до сохранения данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [фиксация внутрипроцессных изменений в элементах управления с привязкой к данным до сохранения данных](https://docs.microsoft.com/visualstudio/data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data).  
  
  
При изменении значения в элементах управления с привязкой к данным, пользователь должен перейти зафиксировать обновленное значение в базовый источник данных, который элемент управления привязывается к текущей записи. При перетаскивании элементов из [окна "Источники данных"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) в форму, первый элемент, перетаскиваемая создает код в **Сохранить** события нажатия кнопки <xref:System.Windows.Forms.BindingNavigator>. Этот код вызывает <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод <xref:System.Windows.Forms.BindingSource>. Таким образом, вызов <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод создается только для первого <xref:System.Windows.Forms.BindingSource> , добавляется в форму.  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Вызов фиксирует все изменения, находящиеся в процессе, во всех элементах управления с привязкой к данным, которые в настоящее время редактируется. Таким образом, если элемент управления с привязкой к данным по-прежнему имеет фокус и нажмите кнопку **Сохранить** кнопку, все ожидающие изменения в этом элементе управления фиксируются до фактического сохранения ( `TableAdapterManager.UpdateAll` метод).  
  
 Можно настроить приложение на автоматическую фиксацию изменений, даже если пользователь пытается сохранить данные без фиксации изменений в процессе сохранения процесса.  
  
> [!NOTE]
>  Конструктор добавляет `BindingSource.EndEdit` код только для первого элемента, помещенной на форму. Таким образом, необходимо добавить строку кода для вызова <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод для каждого <xref:System.Windows.Forms.BindingSource> в форме. Можно вручную добавить строку кода для вызова <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод для каждого <xref:System.Windows.Forms.BindingSource>. Кроме того, можно добавить `EndEditOnAllBindingSources` метод в форму и вызовите его перед выполнением сохранения.  
  
 В следующем коде используется [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) запрос, чтобы выполнять итерации по всем <xref:System.Windows.Forms.BindingSource> компоненты и вызов <xref:System.Windows.Forms.BindingSource.EndEdit%2A> метод для каждого <xref:System.Windows.Forms.BindingSource> в форме.  
  
## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Для вызова EndEdit для всех компонентов BindingSource в форме  
  
1.  Добавьте следующий код в форму, которая содержит <xref:System.Windows.Forms.BindingSource> компонентов.  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]  
  
2.  Добавьте следующую строку кода непосредственно перед любыми вызовами, чтобы сохранить данные формы ( `TableAdapterManager.UpdateAll()` метод):  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>См. также  
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Иерархическое обновление](../data-tools/hierarchical-update.md)

