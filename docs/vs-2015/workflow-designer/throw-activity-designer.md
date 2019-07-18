---
title: Конструктор действия throw | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: db909618971eeab2d92506d1c29b06290aa9263b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976621"
---
# <a name="throw-activity-designer"></a>Конструктор действия Throw
**Throw** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Throw> действия.  
  
## <a name="the-throw-activity"></a>Действие Throw  
 Действие <xref:System.Activities.Statements.Throw> вызывает исключение.  
  
### <a name="using-the-throw-activity-designer"></a>Использование конструктора операций Throw  
 **Throw** конструктора действий можно найти в **обработка ошибок** категории **элементов**, который нажав **элементов**вкладка в левой части [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **Throw** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.Throw> действие по умолчанию **DisplayName** для Throw. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **Throw** конструктора действий или в **DisplayName** поле таблицы свойств. Свойство <xref:System.Activities.Statements.Throw.Exception%2A> должно редактироваться в таблице свойств.  
  
### <a name="the-throw-properties"></a>Свойства Throw  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Throw> и описано их использование в конструкторе.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.Throw>. По умолчанию используется Throw.|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Вызываемое исключение. Данное исключение должно быть производным от класса <xref:System.Exception>. Чтобы указать исключение, введите выражение Visual Basic в таблице свойств.|  
  
## <a name="see-also"></a>См. также  
 [Коллекции](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Конструктор действия throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)