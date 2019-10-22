---
title: Конструктор действия Rethrow | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c65469242a60c64d6f31bfaea4fdbbf2d5251a34
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663359"
---
# <a name="rethrow-activity-designer"></a>Конструктор действия Rethrow
Конструктор действия **Rethrow** используется для создания и настройки действия <xref:System.Activities.Statements.Rethrow>.

## <a name="the-rethrow-activity"></a>Действие Rethrow
 Действие <xref:System.Activities.Statements.Rethrow> вызывает ранее вызванное исключение. Это действие может использоваться только в обработчике <xref:System.Activities.Statements.Catch> в действии <xref:System.Activities.Statements.TryCatch>.

### <a name="using-the-rethrow-activity-designer"></a>Использование конструктора действия ReThrow
 Конструктор действий повторного **создания** можно найти в категории " **Обработка ошибок** " **области элементов**, щелкнув вкладку **область элементов** в левой части [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать **панель инструментов** **в меню** Меню "вид" или CTRL + ALT + X.)

 Конструктор действий **регенерации** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается действие <xref:System.Activities.Statements.Rethrow> со значением **DisplayName** по умолчанию Throw. Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действий **Rethrow** или в поле **DisplayName** сетки свойств.

### <a name="the-rethrow-properties"></a>Свойства Rethrow
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Rethrow> и описано их использование в конструкторе.

|Имя свойства|Обязательное значение|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.Rethrow>. По умолчанию используется Rethrow.|

## <a name="see-also"></a>См. также раздел
 [Коллекция](../workflow-designer/collection-activity-designers.md) [throw](../workflow-designer/throw-activity-designer.md) [TryCatch](../workflow-designer/trycatch-activity-designer.md)