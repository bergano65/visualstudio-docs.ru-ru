---
title: "Диалоговое окно «Редактор коллекции типов» | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 8e4b794a623c3a0218e44773da6bdb6c76612816
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="type-collection-editor-dialog-box"></a>Диалоговое окно редактора коллекций типов
**Редактор коллекции типов** диалоговое окно используется для добавления известных типов в **отправки** и **Receive** действий. Это диалоговое окно также используется для добавления аргументов универсального типа **InvokeMethod** действия. При использовании для **отправки** и **Receive** действий для добавления известных типов **редактор коллекции типов** диалоговом окне требуется тип дополнения, быть уникальным. При добавлении дублирующего типа и подтверждении действия, щелкнув **ОК**, возвращается сообщение об ошибке. При использовании для **InvokeMethod** действия для добавления аргументов универсального типа **редактор коллекции типов** диалогового окна Добавление дублирующих типов.  
  
> [!NOTE]
>  [! ВКЛЮЧИТЬ[crabout](/dotnet/framework/wcf/feature-details/data-contract-known-types).  
  
 В следующей таблице описаны элементы пользовательского интерфейса (UI) **коллекцию типов** диалоговое окно.  
  
|Элемент пользовательского интерфейса|Описание:|  
|----------------|-----------------|  
|**Список типов**|Список добавленных или удаленных типов объектов.|  
  
## <a name="to-bring-up-the-type-collection-editor"></a>Отображение редактора коллекций типов  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Отображение редактора коллекций типов для действий Send и Receive  
  
1.  Выберите **отправки** или **Receive** действий в представлении конструктора.  
  
2.  Нажмите клавишу **F4** для вызова **свойства** окна.  
  
3.  В **свойства** окно, нажмите кнопку с многоточием рядом с **KnownTypes** свойство.  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Отображение редактора коллекций типов для действия InvokeMethod  
  
1.  Выберите **InvokeMethod** действий в представлении конструктора.  
  
2.  Нажмите клавишу **F4** для вызова **свойства** окна.  
  
3.  В **свойства** окно, нажмите кнопку с многоточием рядом с **GenericTypeArguments** свойство.