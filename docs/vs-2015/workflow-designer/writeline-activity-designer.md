---
title: Конструктор действия WriteLine | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c4f656578526879774e698523239d5a9b2b14ccd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657529"
---
# <a name="writeline-activity-designer"></a>Конструктор действия WriteLine
Конструктор действия **WriteLine** используется для создания и настройки <xref:System.Activities.Statements.WriteLine> действия.

## <a name="the-writeline-activity"></a>Операция WriteLine
 Операция <xref:System.Activities.Statements.WriteLine> выполняет запись текста в указанный объект <xref:System.IO.TextWriter>. Если не указано <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.WriteLine> выполняет запись текста к консоли.

### <a name="using-the-writeline-activity-designer"></a>Использование конструктора действий WriteLine
 Конструктор действия **WriteLine** можно найти в категории **примитивы** **панели элементов**, щелкнув вкладку **область элементов** (или выбрав [!INCLUDE[wfd2](../includes/wfd2-md.md)] пункт **панель инструментов** в меню **вид** или нажав клавиши CTRL + ALT + X).

 Конструктор действия **WriteLine** можно перетащить из **области элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . Будет создано действие <xref:System.Activities.Statements.WriteLine> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для WriteLine. <xref:System.Activities.Activity.DisplayName%2A>Можно изменить в заголовке конструктора действия **WriteLine** или в поле **DisplayName** сетки свойств.

### <a name="the-writeline-properties"></a>Свойства WriteLine
 В следующей таблице показаны свойства <xref:System.Activities.Statements.WriteLine> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые из них ― в области конструктора [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Понятное имя действия <xref:System.Activities.Statements.WriteLine>. Значение по умолчанию WriteLine. Для значения <xref:System.Activities.Activity.DisplayName%2A> нет жестких требований, однако лучше всего всегда использовать такое значение.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|Неверно|Текст для записи. Чтобы задать свойство, введите Visual Basic выражение в **текстовом** поле конструктора действий **WriteLine** или в сетке свойств.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|Неверно|Класс <xref:System.IO.TextWriter>, в который <xref:System.Activities.Statements.WriteLine> записывает <xref:System.Activities.Statements.WriteLine.Text%2A>. По умолчанию - консоль.|

## <a name="see-also"></a>См. также:
 [Примитивы](../workflow-designer/primitives-activity-designers.md) [присваивания](../workflow-designer/assign-activity-designer.md) [задержки](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)