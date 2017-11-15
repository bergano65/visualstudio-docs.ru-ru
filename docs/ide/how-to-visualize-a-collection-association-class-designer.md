---
title: "Практическое руководство. Визуализация ассоциации коллекции (конструктор классов) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 53eb6ed7e8025ee6cc9a9a3ee8161078accbc457
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-visualize-a-collection-association-class-designer"></a>Практическое руководство. Визуализация ассоциации коллекции в конструкторе класса (конструктор классов)
Свойства и поля, которые являются наборами других типов, могут отображаться в схеме классов как ассоциация набора. В отличие от обычной ассоциации, которая отображает поля или свойства в виде линии, связывающей класс-владелец с типом поля, ассоциация набора отображается как линия, связывающая класс-владелец с собранным типом.  
  
### <a name="to-create-a-collection-association"></a>Создание ассоциации набора  
  
1.  В коде создайте свойство или поле, тип которого является строго типизированным набором.  
  
2.  В схеме классов разверните класс так, чтобы отображались свойства и поля.  
  
3.  В классе щелкните правой кнопкой мыши поле или свойство и выберите **Показывать как ассоциацию наборов**.  
  
     Свойство или поле отображается в виде линии ассоциации, связанной с собранным типом.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Создание ассоциаций между типами (конструктор классов)](../ide/how-to-create-associations-between-types-class-designer.md)   
 [Конструирование классов и типов (конструктор классов)](../ide/designing-classes-and-types-class-designer.md)   
 [Просмотр типов и отношений (конструктор классов)](../ide/viewing-types-and-relationships-class-designer.md)