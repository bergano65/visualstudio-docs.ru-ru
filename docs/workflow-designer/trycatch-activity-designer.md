---
title: Конструктор рабочих процессов - конструктора действий TryCatch
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2983dd9aa53443c616504672ef76f76ac9bd9add
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="trycatch-activity-designer"></a>Конструктор действия «TryCatch»

**TryCatch** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.TryCatch> действия.

## <a name="the-trycatch-activity"></a>Действие TryCatch
 <xref:System.Activities.Statements.TryCatch> Действие содержит <xref:System.Activities.Statements.TryCatch.Try%2A> действия, набор **перехватывать\<TException >** и <xref:System.Activities.Statements.TryCatch.Finally%2A> действия. Объект <xref:System.Activities.Statements.Catch%601> типа **TException** содержит <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> и <xref:System.Activities.Statements.Catch%601.Action%2A>. Оба они используются для реализации обработки типичных ошибок, основанной на исключении. Действие <xref:System.Activities.Statements.TryCatch> пытается выполнить свое действие <xref:System.Activities.Statements.TryCatch.Try%2A>. Если <xref:System.Activities.Statements.TryCatch.Try%2A> действие создает исключение, <xref:System.Activities.Statements.TryCatch> действие использует его **перехватывать < TException\>**  коллекции для сопоставления исключения. Если соответствие, то <xref:System.Activities.Statements.Catch%601.Action%2A> соответствующего **перехватывать\<TException >** выполняется, выступают в качестве обработки логики для исключения ошибок. Если действия в разделе <xref:System.Activities.Statements.TryCatch.Try%2A> или <xref:System.Activities.Statements.TryCatch.Catches%2A> успешно выполняются, действие <xref:System.Activities.Statements.TryCatch> выполняет свое действие <xref:System.Activities.Statements.TryCatch.Finally%2A>. Дополнительные сведения см. в разделе [исключения рабочего процесса Windows](/dotnet/framework/windows-workflow-foundation/exceptions).

### <a name="using-the-trycatch-activity-designer"></a>Использование конструктора действий TryCatch
 **TryCatch** конструктора действий можно найти в **обработка ошибок** категории **элементов**, который нажав **элементов** вкладка в левой части конструктора рабочих процессов (либо выберите **инструментов** из **представление** меню или CTLR + ALT + X.)

 **TryCatch** конструктора можно перетащить из **элементов** и удалена на поверхности конструктора рабочих процессов, везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.TryCatch> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для TryCatch. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **TryCatch** конструктора или в **DisplayName** поле сетки свойств. Другие свойства необходимо изменять на поверхности **TryCatch** конструктора действий.

 Нажмите кнопку «развернуть» в правом верхнем углу **TryCatch** конструктор, чтобы просмотреть **повторите**, **перехватывает**, и **наконец** окнам в средах Расширенное представление. Чтобы добавить критерий обнаружения, нажмите кнопку **добавить новый перехват** кнопку **TryCatch** конструктора. Кнопка преобразуется в поле со списком, в котором можно вводить текст. Выберите тип исключения и нажмите ВВОД, чтобы добавить критерий перехвата. После добавления **перехватывать**, область критерия перехвата разворачивается и действия можно перетащить в catch, чтобы определить логику выполнения для критерия перехвата. Обратите внимание на текстовое поле с правой стороны развернутой области критериев. При помощи этого текстового поля можно назвать переменную исключения. Переменная исключения может использоваться только для действий внутри одного **перехватывать**.

 **TryCatch** конструктор не поддерживает редактирование **перехватывать**. Если вы хотите изменить тип исключения, вы должны удалить **перехватывать** и добавить новую. Объект **перехватывать** можно удалить, выбрав его и ее удаление или с помощью **удалить** меню, в контекстном меню, нажав правой.

### <a name="the-trycatch-properties"></a>Свойства TryCatch
 В следующей таблице показаны <xref:System.Activities.Statements.TryCatch>свойства и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.TryCatch>. Значение по умолчанию: TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Действие, выполняемое первым при выполнении действия <xref:System.Activities.Statements.TryCatch>.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Коллекция **перехватывать** элементы, которые проверяются, когда <xref:System.Activities.Statements.TryCatch.Try%2A> действие создает исключение.<br /><br /> Требуется добавить по крайней мере одно действие в блок <xref:System.Activities.Statements.TryCatch.Catches%2A> или в блок <xref:System.Activities.Statements.TryCatch.Finally%2A>.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Действие, которое необходимо выполнить, когда завершится выполнение <xref:System.Activities.Statements.TryCatch.Try%2A> и любых необходимых действий в коллекции <xref:System.Activities.Statements.TryCatch.Catches%2A>.<br /><br /> Требуется добавить по крайней мере одно действие в блок <xref:System.Activities.Statements.TryCatch.Catches%2A> или в блок <xref:System.Activities.Statements.TryCatch.Finally%2A>.|

## <a name="see-also"></a>См. также

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [заново создать](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)