---
title: Конструктор рабочих процессов - конструктор действия TryCatch
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
ms.openlocfilehash: 26985893ae5a6431743564e28793957ecf0f9e01
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756818"
---
# <a name="trycatch-activity-designer"></a>Конструктор действия «TryCatch»

**TryCatch** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.TryCatch> действия.

## <a name="the-trycatch-activity"></a>Действие TryCatch
 <xref:System.Activities.Statements.TryCatch> Действие содержит <xref:System.Activities.Statements.TryCatch.Try%2A> действия, набор **Catch\<TException >** и <xref:System.Activities.Statements.TryCatch.Finally%2A> действия. Объект <xref:System.Activities.Statements.Catch%601> типа **TException** содержит <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> и <xref:System.Activities.Statements.Catch%601.Action%2A>. Оба они используются для реализации обработки типичных ошибок, основанной на исключении. Действие <xref:System.Activities.Statements.TryCatch> пытается выполнить свое действие <xref:System.Activities.Statements.TryCatch.Try%2A>. Если <xref:System.Activities.Statements.TryCatch.Try%2A> действие создает исключение, <xref:System.Activities.Statements.TryCatch> действие использует его **Catch < TException\>**  коллекции для сопоставления исключения. Если есть совпадение имени, а затем <xref:System.Activities.Statements.Catch%601.Action%2A> соответствующего **Catch\<TException >** выполняется, выступая в качестве логической исключения для обработки. Если действия в разделе <xref:System.Activities.Statements.TryCatch.Try%2A> или <xref:System.Activities.Statements.TryCatch.Catches%2A> успешно выполняются, действие <xref:System.Activities.Statements.TryCatch> выполняет свое действие <xref:System.Activities.Statements.TryCatch.Finally%2A>. Дополнительные сведения см. в разделе [исключения рабочего процесса Windows](/dotnet/framework/windows-workflow-foundation/exceptions).

### <a name="using-the-trycatch-activity-designer"></a>Использование конструктора действий TryCatch

Доступ **TryCatch** конструктора действий в **обработка ошибок** категории **элементов**.

**TryCatch** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.TryCatch> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для TryCatch. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **TryCatch** конструктора действий или в **DisplayName** поле таблицы свойств. Другие свойства следует изменять в области **TryCatch** конструктора действий.

Нажмите кнопку "Развернуть" в правом верхнем углу **TryCatch** конструктору см. в разделе **попробуйте**, **перехватывает**, и **наконец** окнам в средах Расширенное представление. Чтобы добавить критерий обнаружения, нажмите кнопку **добавить новый перехват** кнопку **TryCatch** конструктора. Кнопка преобразуется в поле со списком, в котором можно вводить текст. Выберите тип исключения и нажмите ВВОД, чтобы добавить критерий перехвата. После добавления **Catch**, расширяет область критерия перехвата и действия можно перетаскивать в catch, чтобы определить логику выполнения для catch. Обратите внимание на текстовое поле с правой стороны развернутой области критериев. При помощи этого текстового поля можно назвать переменную исключения. Переменная исключения может использоваться только для действий внутри одного **Catch**.

**TryCatch** конструктор не поддерживает изменение **Catch**. Если вы хотите изменить тип исключения, необходимо удалить **Catch** и добавить новую. Объект **Catch** можно удалить, выбрав его и удалив его или используя **удалить** меню в контекстном меню, нажав правой кнопкой мыши.

### <a name="the-trycatch-properties"></a>Свойства TryCatch

В следующей таблице показаны <xref:System.Activities.Statements.TryCatch>свойства и показывается, как они используются в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.TryCatch>. Значение по умолчанию: TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Действие, выполняемое первым при выполнении действия <xref:System.Activities.Statements.TryCatch>.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Коллекция **Catch** элементов, которые проверяются, когда <xref:System.Activities.Statements.TryCatch.Try%2A> действие выдает исключение.<br /><br /> Требуется добавить по крайней мере одно действие в блок <xref:System.Activities.Statements.TryCatch.Catches%2A> или в блок <xref:System.Activities.Statements.TryCatch.Finally%2A>.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Действие, которое необходимо выполнить, когда завершится выполнение <xref:System.Activities.Statements.TryCatch.Try%2A> и любых необходимых действий в коллекции <xref:System.Activities.Statements.TryCatch.Catches%2A>.<br /><br /> Требуется добавить по крайней мере одно действие в блок <xref:System.Activities.Statements.TryCatch.Catches%2A> или в блок <xref:System.Activities.Statements.TryCatch.Finally%2A>.|

## <a name="see-also"></a>См. также

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)