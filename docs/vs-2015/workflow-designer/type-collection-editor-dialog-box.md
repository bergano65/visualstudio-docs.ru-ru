---
title: Диалоговое окно «Редактор коллекции типов» | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8f3b536ff59c01e1be71bd0fcfb57946219cefd1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073077"
---
# <a name="type-collection-editor-dialog-box"></a>Диалоговое окно редактора коллекций типов
**Редактор коллекции типов** диалоговое окно используется для добавления известных типов для **отправки** и **Receive** действий. Это диалоговое окно также используется для добавления аргументов универсального типа для **InvokeMethod** действия. При использовании для **отправки** и **Receive** действия для добавления известных типов **редактор коллекции типов** диалоговое окно требует добавления типов должны быть уникальными. При добавлении дублирующего типа и подтверждении, нажав кнопку **ОК**, возвращается сообщение об ошибке. При использовании для **InvokeMethod** действия для добавления аргументов универсального типа, **редактор коллекции типов** диалоговое окно позволяет добавлять дублирующих типов.  
  
> [!NOTE]
>  [!INCLUDE[crabout](../includes/crabout-md.md)] об известных типах см. в разделе [Data Contract Known Types](http://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337).  
  
 В следующей таблице описаны элементы пользовательского интерфейса (UI) **коллекция типов** диалоговое окно.  
  
|Элемент пользовательского интерфейса|Описание|  
|----------------|-----------------|  
|**Список типов**|Список добавленных или удаленных типов объектов.|  
  
## <a name="to-bring-up-the-type-collection-editor"></a>Отображение редактора коллекций типов  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Отображение редактора коллекций типов для действий Send и Receive  
  
1. Выберите **отправки** или **Receive** действий в представлении конструктора.  
  
2. Нажмите клавишу **F4** откроется **свойства** окна.  
  
3. В **свойства** окно, нажмите кнопку с многоточием, расположенную рядом с полем **KnownTypes** свойство.  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Отображение редактора коллекций типов для действия InvokeMethod  
  
1. Выберите **InvokeMethod** действий в представлении конструктора.  
  
2. Нажмите клавишу **F4** откроется **свойства** окна.  
  
3. В **свойства** окно, нажмите кнопку с многоточием, расположенную рядом с полем **GenericTypeArguments** свойство.