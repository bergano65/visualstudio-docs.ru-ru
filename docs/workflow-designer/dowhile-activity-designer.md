---
title: "Конструктор действия DoWhile | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 041c63d45e70305495fd18ed595a31eee6772389
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="dowhile-activity-designer"></a>Конструктор действия DoWhile
<xref:System.Activities.Statements.DoWhile> Действия выполняет действие, содержащееся в его <xref:System.Activities.Statements.DoWhile.Body%2A> по крайней мере один раз, пока заданное условие не примет значение **false**. Если необходимо, чтобы действие, содержащееся в теле цикла, выполнялось ноль или более раз, используйте действие <xref:System.Activities.Statements.While>.  
  
## <a name="dowhile-properties-in-the-workflow-designer"></a>Свойства DoWhile в конструкторе рабочих процессов  
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.DoWhile>, которые применяются чаще всего, и описано их использование в конструкторе.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Действие, выполняемое, пока условие имеет **true**. Чтобы добавить <xref:System.Activities.Statements.DoWhile.Body%2A> действие, перетащите действие из панели элементов в **текст** поле на **DoWhile** конструктора действий с текстом подсказки «Перетащить действие сюда».|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Да|Условие оценивается после каждой итерации цикла. Чтобы задать <xref:System.Activities.Statements.DoWhile.Condition%2A>, введите значение [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] выражение в **условие** поле на **DoWhile** действие конструктора или в сетке свойств.|  
  
## <a name="see-also"></a>См. также  
 [While](../workflow-designer/while-activity-designer.md)   
 [Поток управления](../workflow-designer/control-flow-activity-designers.md)