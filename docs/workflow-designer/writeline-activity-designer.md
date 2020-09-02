---
title: Конструктор действия конструктор рабочих процессов-WriteLine
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e3b4da69a2d9154f36e42d3b20657e204767872
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593028"
---
# <a name="writeline-activity-designer"></a>Конструктор действия WriteLine

Конструктор действия **WriteLine** используется для создания и настройки <xref:System.Activities.Statements.WriteLine> действия.

## <a name="the-writeline-activity"></a>Операция WriteLine

Операция <xref:System.Activities.Statements.WriteLine> выполняет запись текста в указанный объект <xref:System.IO.TextWriter>. Если не указано <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.WriteLine> выполняет запись текста к консоли.

### <a name="using-the-writeline-activity-designer"></a>Использование конструктора действий WriteLine

Доступ к конструктору действия **WriteLine** в категории **примитивы** **панели элементов**. Конструктор действий **WriteLine** можно перетащить из **панели элементов** в конструктор рабочих процессов область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . Будет создано действие <xref:System.Activities.Statements.WriteLine> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для WriteLine. <xref:System.Activities.Activity.DisplayName%2A>Можно изменить в заголовке конструктора действия **WriteLine** или в поле **DisplayName** сетки свойств.

### <a name="the-writeline-properties"></a>Свойства WriteLine

В следующей таблице показаны свойства <xref:System.Activities.Statements.WriteLine> и описано их использование в конструкторе. Эти свойства можно изменять в сетке свойств, а некоторые из них можно редактировать на конструктор рабочих процессов поверхности.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Понятное имя действия <xref:System.Activities.Statements.WriteLine>. Значение по умолчанию WriteLine. Для значения <xref:System.Activities.Activity.DisplayName%2A> нет жестких требований, однако лучше всего всегда использовать такое значение.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|Неверно|Текст для записи. Чтобы задать свойство, введите Visual Basic выражение в **текстовом** поле конструктора действий **WriteLine** или в сетке свойств.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|Неверно|Класс <xref:System.IO.TextWriter>, в который <xref:System.Activities.Statements.WriteLine> записывает <xref:System.Activities.Statements.WriteLine.Text%2A>. По умолчанию - консоль.|

## <a name="see-also"></a>См. также раздел

- [Примитивы](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Задержка](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
