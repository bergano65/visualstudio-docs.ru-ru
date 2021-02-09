---
title: Конструктор действий конструктор рабочих процессов TryCatch
description: Сведения о действии TryCatch и о том, как можно использовать конструктор действий TryCatch для создания и настройки действия TryCatch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 23d9f1b0037600c6612a413cce7b089f6adbc7aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889308"
---
# <a name="trycatch-activity-designer"></a>Конструктор действия «TryCatch»

Конструктор действий **TryCatch** используется для создания и настройки <xref:System.Activities.Statements.TryCatch> действия.

## <a name="the-trycatch-activity"></a>Действие TryCatch
 <xref:System.Activities.Statements.TryCatch>Действие содержит <xref:System.Activities.Statements.TryCatch.Try%2A> действие, коллекцию **Catch \<TException>** и <xref:System.Activities.Statements.TryCatch.Finally%2A> действие. Объект <xref:System.Activities.Statements.Catch%601> типа **тексцептион** содержит <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> и <xref:System.Activities.Statements.Catch%601.Action%2A> . Оба они используются для реализации обработки типичных ошибок, основанной на исключении. Действие <xref:System.Activities.Statements.TryCatch> пытается выполнить свое действие <xref:System.Activities.Statements.TryCatch.Try%2A>. Если <xref:System.Activities.Statements.TryCatch.Try%2A> действие создает исключение, <xref:System.Activities.Statements.TryCatch> действие использует коллекцию **catch<тексцептион \>** для сопоставления исключения. Если найдено совпадение, то <xref:System.Activities.Statements.Catch%601.Action%2A> выполняется соответствующий **блок Catch \<TException>** , который служит логикой обработки ошибок для исключения. Если действия в разделе <xref:System.Activities.Statements.TryCatch.Try%2A> или <xref:System.Activities.Statements.TryCatch.Catches%2A> успешно выполняются, действие <xref:System.Activities.Statements.TryCatch> выполняет свое действие <xref:System.Activities.Statements.TryCatch.Finally%2A>. Дополнительные сведения см. в статье [исключения рабочих процессов Windows](/dotnet/framework/windows-workflow-foundation/exceptions).

### <a name="using-the-trycatch-activity-designer"></a>Использование конструктора действий TryCatch

Доступ к конструктору действий **TryCatch** в категории " **Обработка ошибок** " **панели элементов**.

Конструктор действий **TryCatch** можно перетащить из **панели элементов** в область Конструктор рабочих процессов, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . Будет создано действие <xref:System.Activities.Statements.TryCatch> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для TryCatch. <xref:System.Activities.Activity.DisplayName%2A>Значение можно изменить в заголовке конструктора действий **TryCatch** или в поле **DisplayName** сетки свойств. Другие свойства должны быть изменены на поверхности конструктора действий **TryCatch** .

Нажмите кнопку развернуть в правом верхнем углу конструктора **TryCatch** , чтобы увидеть поля **try**, **catch** и **finally** в развернутом представлении. Чтобы добавить catch, нажмите кнопку **Добавить новую кнопку catch** в конструкторе **TryCatch** . Кнопка преобразуется в поле со списком, в котором можно вводить текст. Выберите тип исключения и нажмите ВВОД, чтобы добавить критерий перехвата. После добавления **блока** catch область catch разворачивается, а действие можно перетащить в блок catch, чтобы определить логику выполнения для catch. Обратите внимание на текстовое поле с правой стороны of развернутой области критериев. При помощи этого текстового поля можно назвать переменную исключения. Переменная исключения может использоваться только для действий в одном и том же **перехвате**.

Конструктор **TryCatch** не поддерживает редактирование **catch**. Если необходимо изменить тип исключения, необходимо удалить **перехват** и добавить новый. Чтобы удалить **catch** , выберите его и удалите или выбрав пункт **Удалить** в контекстном меню, доступном щелчке правой кнопкой мыши.

### <a name="the-trycatch-properties"></a>Свойства TryCatch

В следующей таблице показаны <xref:System.Activities.Statements.TryCatch> Свойства и описано, как они используются в конструкторе.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.TryCatch>. Значение по умолчанию: TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Действие, выполняемое первым при выполнении действия <xref:System.Activities.Statements.TryCatch>.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Коллекция элементов **catch** , проверяемых, когда <xref:System.Activities.Statements.TryCatch.Try%2A> действие создает исключение.<br /><br /> Требуется добавить по крайней мере одно действие в блок <xref:System.Activities.Statements.TryCatch.Catches%2A> или в блок <xref:System.Activities.Statements.TryCatch.Finally%2A>.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Действие, которое необходимо выполнить, когда завершится выполнение <xref:System.Activities.Statements.TryCatch.Try%2A> и любых необходимых действий в коллекции <xref:System.Activities.Statements.TryCatch.Catches%2A>.<br /><br /> Требуется добавить по крайней мере одно действие в блок <xref:System.Activities.Statements.TryCatch.Catches%2A> или в блок <xref:System.Activities.Statements.TryCatch.Finally%2A>.|

## <a name="see-also"></a>См. также раздел

- [Коллекция](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Даче](../workflow-designer/throw-activity-designer.md)
