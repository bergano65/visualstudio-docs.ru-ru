---
title: Конструктор действия Throw | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1855daa5016241fb6eb04f05d7218e02083fc0a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655165"
---
# <a name="throw-activity-designer"></a>Конструктор действия Throw
Конструктор действия **throw** используется для создания и настройки <xref:System.Activities.Statements.Throw> действия.

## <a name="the-throw-activity"></a>Действие Throw
 Действие <xref:System.Activities.Statements.Throw> вызывает исключение.

### <a name="using-the-throw-activity-designer"></a>Использование конструктора операций Throw
 Конструктор действия **throw** можно найти в категории **Обработка ошибок** **области элементов**, щелкнув вкладку **область элементов** в левой части окна [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать пункт **панель инструментов** в меню **вид** или CTRL + ALT + X).

 Конструктор действий **throw** можно перетащить из **области элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . При этом создается <xref:System.Activities.Statements.Throw> действие со значением **DisplayName** по умолчанию Throw. <xref:System.Activities.Activity.DisplayName%2A>Значение можно изменить в заголовке конструктора действий **throw** или в поле **DisplayName** сетки свойств. Свойство <xref:System.Activities.Statements.Throw.Exception%2A> должно редактироваться в таблице свойств.

### <a name="the-throw-properties"></a>Свойства Throw
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Throw> и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.Throw>. По умолчанию используется Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|Верно|Вызываемое исключение. Данное исключение должно быть производным от класса <xref:System.Exception>. Чтобы указать исключение, введите выражение Visual Basic в таблице свойств.|

## <a name="see-also"></a>См. также:
 Повторная генерация [коллекции](../workflow-designer/collection-activity-designers.md) [Rethrow](../workflow-designer/rethrow-activity-designer.md) [действия Throw](../workflow-designer/throw-activity-designer.md) [TryCatch](../workflow-designer/trycatch-activity-designer.md)