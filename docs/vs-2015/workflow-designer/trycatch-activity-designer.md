---
title: Конструктор действий TryCatch | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b26bb37d1ddeabb77b1399c6cbce5ae55b59702c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654662"
---
# <a name="trycatch-activity-designer"></a>Конструктор действия «TryCatch»
Конструктор действий **TryCatch** используется для создания и настройки действия <xref:System.Activities.Statements.TryCatch>.

## <a name="the-trycatch-activity"></a>Действие TryCatch
 Действие <xref:System.Activities.Statements.TryCatch> содержит <xref:System.Activities.Statements.TryCatch.Try%2A> действие, коллекцию **\<TException >** и действие <xref:System.Activities.Statements.TryCatch.Finally%2A>. @No__t_0 типа **тексцептион** содержит <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> и <xref:System.Activities.Statements.Catch%601.Action%2A>. Оба они используются для реализации обработки типичных ошибок, основанной на исключении. Действие <xref:System.Activities.Statements.TryCatch> пытается выполнить свое действие <xref:System.Activities.Statements.TryCatch.Try%2A>. Если <xref:System.Activities.Statements.TryCatch.Try%2A> действие создает исключение, действие <xref:System.Activities.Statements.TryCatch> использует для сопоставления этого исключения коллекцию **Catch < тексцептион \>** . При совпадении выполняется <xref:System.Activities.Statements.Catch%601.Action%2A> соответствующего **> Catch \<TException** , который служит логикой обработки ошибок для исключения. Если действия в разделе <xref:System.Activities.Statements.TryCatch.Try%2A> или <xref:System.Activities.Statements.TryCatch.Catches%2A> успешно выполняются, действие <xref:System.Activities.Statements.TryCatch> выполняет свое действие <xref:System.Activities.Statements.TryCatch.Finally%2A>. [!INCLUDE[crdefault](../includes/crdefault-md.md)][исключения](https://msdn.microsoft.com/library/065205cc-52dd-4f30-9578-b17d8d113136).

### <a name="using-the-trycatch-activity-designer"></a>Использование конструктора действий TryCatch
 Конструктор действий **TryCatch** можно найти в категории **Обработка ошибок** **области элементов**, щелкнув вкладку **область элементов** в левой части [!INCLUDE[wfd2](../includes/wfd2-md.md)] (или выбрать **панель инструментов** **в меню** Меню "вид" или "ктлр + ALT + X".)

 Конструктор действий **TryCatch** можно перетащить из **панели элементов** в область [!INCLUDE[wfd2](../includes/wfd2-md.md)], где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.TryCatch> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для TryCatch. Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действий **TryCatch** или в поле **DisplayName** сетки свойств. Другие свойства должны быть изменены на поверхности конструктора действий **TryCatch** .

 Нажмите кнопку развернуть в правом верхнем углу конструктора **TryCatch** , чтобы увидеть поля **try**, **catch**и **finally** в развернутом представлении. Чтобы добавить catch, нажмите кнопку **Добавить новую кнопку catch** в конструкторе **TryCatch** . Кнопка преобразуется в поле со списком, в котором можно вводить текст. Выберите тип исключения и нажмите ВВОД, чтобы добавить критерий перехвата. После добавления **блока**catch область catch разворачивается, а действие можно перетащить в блок catch, чтобы определить логику выполнения для catch. Обратите внимание на текстовое поле с правой стороны of развернутой области критериев. При помощи этого текстового поля можно назвать переменную исключения. Переменная исключения может использоваться только для действий в одном и том же **перехвате**.

 Конструктор **TryCatch** не поддерживает редактирование **catch**. Если необходимо изменить тип исключения, необходимо удалить **перехват** и добавить новый. Чтобы удалить **catch** , выберите его и удалите или с помощью меню **Удалить** в контекстном меню, доступном щелчке правой кнопкой мыши.

### <a name="the-trycatch-properties"></a>Свойства TryCatch
 В следующей таблице показаны <xref:System.Activities.Statements.TryCatch>properties и описано, как они используются в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.TryCatch>. Значение по умолчанию: TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Действие, выполняемое первым при выполнении действия <xref:System.Activities.Statements.TryCatch>.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Коллекция элементов **catch** , проверяемых, когда действие <xref:System.Activities.Statements.TryCatch.Try%2A> создает исключение.<br /><br /> Требуется добавить по крайней мере одно действие в блок <xref:System.Activities.Statements.TryCatch.Catches%2A> или в блок <xref:System.Activities.Statements.TryCatch.Finally%2A>.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Действие, которое необходимо выполнить, когда завершится выполнение <xref:System.Activities.Statements.TryCatch.Try%2A> и любых необходимых действий в коллекции <xref:System.Activities.Statements.TryCatch.Catches%2A>.<br /><br /> Требуется добавить по крайней мере одно действие в блок <xref:System.Activities.Statements.TryCatch.Catches%2A> или в блок <xref:System.Activities.Statements.TryCatch.Finally%2A>.|

## <a name="see-also"></a>См. также
 [Повторная](../workflow-designer/throw-activity-designer.md) [генерация](../workflow-designer/rethrow-activity-designer.md) [коллекции](../workflow-designer/collection-activity-designers.md)