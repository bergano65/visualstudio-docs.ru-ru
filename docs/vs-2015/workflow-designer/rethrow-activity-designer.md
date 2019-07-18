---
title: Конструктор действия rethrow | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8b023a42da1c862927606c4bec0215120a5e5a11
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62937761"
---
# <a name="rethrow-activity-designer"></a>Конструктор действия Rethrow
**Rethrow** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Rethrow> действия.  
  
## <a name="the-rethrow-activity"></a>Действие Rethrow  
 Действие <xref:System.Activities.Statements.Rethrow> вызывает ранее вызванное исключение. Это действие может использоваться только в обработчике <xref:System.Activities.Statements.Catch> в действии <xref:System.Activities.Statements.TryCatch>.  
  
### <a name="using-the-rethrow-activity-designer"></a>Использование конструктора действия ReThrow  
 **Rethrow** конструктора действий можно найти в **обработка ошибок** категории **элементов**, который нажав **элементов**вкладка в левой части [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **Rethrow** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.Rethrow> действие по умолчанию **DisplayName** для Throw. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **Rethrow** конструктора действий или в **DisplayName** поле таблицы свойств.  
  
### <a name="the-rethrow-properties"></a>Свойства Rethrow  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Rethrow> и описано их использование в конструкторе.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.Rethrow>. По умолчанию используется Rethrow.|  
  
## <a name="see-also"></a>См. также  
 [Коллекции](../workflow-designer/collection-activity-designers.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)