---
title: Конструктор действия DoWhile | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d09954409baccfdc5d9eb083a15bd02f5d16cb85
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989766"
---
# <a name="dowhile-activity-designer"></a>Конструктор действия DoWhile
<xref:System.Activities.Statements.DoWhile> Действия выполняет действие, содержащееся в его <xref:System.Activities.Statements.DoWhile.Body%2A> по крайней мере один раз, пока заданное условие не примет значение **false**. Если необходимо, чтобы действие, содержащееся в теле цикла, выполнялось ноль или более раз, используйте действие <xref:System.Activities.Statements.While>.  
  
## <a name="dowhile-properties-in-the-workflow-designer"></a>Свойства DoWhile в конструкторе рабочих процессов  
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.DoWhile>, которые применяются чаще всего, и описано их использование в конструкторе.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Действие, которое выполняется, пока условие имеет **true**. Чтобы добавить <xref:System.Activities.Statements.DoWhile.Body%2A> действие, перетащите его из области элементов в **текст** поле **DoWhile** конструктора действий с текстом подсказки «Перетащить действие сюда».|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Условие оценивается после каждой итерации цикла. Чтобы задать <xref:System.Activities.Statements.DoWhile.Condition%2A>, введите значение [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] выражение в **условие** поле **DoWhile** действие конструктора или в сетке свойств.|  
  
## <a name="see-also"></a>См. также  
 [во время](../workflow-designer/while-activity-designer.md)   
 [Поток управления](../workflow-designer/control-flow-activity-designers.md)