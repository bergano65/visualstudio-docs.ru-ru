---
title: "Конструктор действия send | Документы Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 22ad913623480599f8d299cba438b108a4511ae7
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2018
---
# <a name="send-activity-designer"></a>Конструктор действия Send

**Отправки** конструктора действий используется для создания и настройки <xref:System.ServiceModel.Activities.Send> действия.

## <a name="the-send-activity"></a>Действие Send
 Действие <xref:System.ServiceModel.Activities.Send> предназначено для отправки сообщения службе. Действие <xref:System.ServiceModel.Activities.ReceiveReply> может быть привязано к действию <xref:System.ServiceModel.Activities.Send>, которое получает сообщение в процессе обмена сообщениями по шаблону «запрос-ответ» на стороне клиента.

### <a name="using-the-send-activity-designer"></a>Использование конструктора действия Send
 **Отправки** конструктора действий можно найти в **обмен сообщениями** категории **элементов**, которой нажав **элементов** вкладки в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

 **Отправки** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] , где обычно размещаются действия. Будет создано действие <xref:System.ServiceModel.Activities.Send> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> Send. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **отправки** конструктора или в **DisplayName** поле сетки свойств.

 Для создания <xref:System.ServiceModel.Activities.ReceiveReply> действия и привяжите его к выбранному <xref:System.ServiceModel.Activities.Send> действия, щелкните правой кнопкой мыши **отправки** конструктора, щелкните действие **создать ReceiveReply** элемента в контекстном меню и **ReceiveReplyForSend** появится ниже конструктора **отправки** конструктора. Действие <xref:System.ServiceModel.Activities.ReceiveReply> получает сообщение в процессе обмена сообщениями по шаблону «запрос-ответ» на стороне клиента. Он может быть настроен с **ReceiveReplyForSend** конструктора.

 Кроме того **SendAndReceiveReply** конструктора шаблонов в **обмен сообщениями** категории **элементов** можно использовать для создания пары предварительно настроенных <xref:System.ServiceModel.Activities.Send>и <xref:System.ServiceModel.Activities.ReceiveReply> действий. Дополнительные сведения об использовании **SendAndReceiveReply** и **ReceiveReplyForSend** шаблонов, см. раздел [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) раздела.

### <a name="the-send-activity-properties"></a>Свойства действия Send
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.Send> и описано их использование в конструкторе. Эти свойства могут быть изменены в таблице свойств или в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.ServiceModel.Activities.Send>. Значение по умолчанию - Send. Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.ServiceModel.Activities.Send.OperationName%2A>|True|Имя операции службы, вызываемой этим действием <xref:System.ServiceModel.Activities.Send>. Это свойство используется для создания значения по умолчанию для **действия** свойство Если **действия** свойство не задано явно.|
|<xref:System.ServiceModel.Activities.Send.ServiceContractName%2A>|Да|Имя контракта службы, который реализуется вызываемой службой.|
|<xref:System.ServiceModel.Activities.Send.Content%2A>|False|Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Это свойство можно изменить, нажав кнопку с многоточием рядом с **содержимого** в таблице свойств или нажав кнопку **определение...**  рядом **содержимого** метки на **Receive** области конструктора операций. Как отобразить **определение содержимого** диалогового окна. Дополнительные сведения о том, как использовать это поле в разделе [содержимого диалоговое окно Определение](../workflow-designer/content-definition-dialog-box.md) раздела.|
|<xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A>|False|Задает метод <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для перенаправления сообщения в соответствующий экземпляр рабочего процесса.<br /><br /> Нажмите кнопку с многоточием рядом с <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> свойства в сетке свойств, чтобы открыть **редактор выражений** диалоговое окно. Дополнительные сведения об использовании этого диалогового окна см. в разделе [способов: с помощью редактора выражений](../workflow-designer/how-to-use-the-expression-editor.md) раздела.|
|<xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A>|False|Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Send> в рамках рабочего процесса. Нажмите кнопку с многоточием рядом с <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> свойства в сетке свойств, чтобы открыть **Добавление инициализаторов корреляции** диалоговое окно. Дополнительные сведения об использовании этого поля в разделе [CorrelationInitializers диалоговое окно Добавление](../workflow-designer/add-correlationinitializers-dialog-box.md) раздела.|
|<xref:System.ServiceModel.Activities.Send.KnownTypes%2A>|False|Коллекция известных типов для операции службы, вызываемой этим действием <xref:System.ServiceModel.Activities.Send>. Это свойство должно использоваться вместе со свойством <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>, установленным в значение <xref:System.Runtime.Serialization.DataContractSerializer>. Не учитывается, если используется <xref:System.Xml.Serialization.XmlSerializer>.<br /><br /> Нажмите кнопку с многоточием рядом с **KnownTypes** в таблице свойств для отображения **редактор коллекции типов** диалоговое окно, с помощью которого можно добавить необходимые типы.<br /><br /> Нажмите кнопку с многоточием рядом с **KnownTypes** в таблице свойств для отображения **редактор коллекции типов** диалоговое окно с помощью которого можно добавить необходимые типы. Дополнительные сведения об использовании этого поля в разделе [диалоговое окно редактора коллекции типа](../workflow-designer/type-collection-editor-dialog-box.md) раздела.|
|<xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A>|Да|Задает <xref:System.Net.Security.ProtectionLevel> для сообщения.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> означает только проверку подлинности.<br />2. <xref:System.Net.Security.ProtectionLevel> означает необходимость подписи данных для обеспечения целостности передаваемых данных.<br />3. <xref:System.Net.Security.ProtectionLevel> означает необходимость шифрования и подписи данных для обеспечения конфиденциальности и целостности передаваемых данных.|
|<xref:System.ServiceModel.Activities.Send.SerializerOption%2A>|Да|Сериализатор, используемый для этой операции службы, вызываемой действием <xref:System.ServiceModel.Activities.Send>. Значение по умолчанию - <xref:System.Runtime.Serialization.DataContractSerializer>, при котором производится сериализация и десериализация экземпляра типа в XML-поток или документ с использованием переданного контракта данных.|
|<xref:System.ServiceModel.Activities.Send.Action%2A>|False|Указывает заголовок действия сообщения. Если оно не задано явно, его значение по умолчанию: https://tempuri.org/ {пространство имен контракта службы} / {имя контракта службы} / {имя операции}. Если задано для действия <xref:System.ServiceModel.Activities.Send>, то для успешной доставки сообщения действие <xref:System.ServiceModel.Activities.Receive>, принимающее сообщение, должно иметь то же значение.|
|<xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A>||<xref:System.Security.Principal.TokenImpersonationLevel>, допустимое для получателя сообщения. Определяет уровни олицетворения безопасности, указывающие степень, до которой серверный процесс может действовать от лица клиентского процесса. <xref:System.Security.Principal.TokenImpersonationLevel> указывает, что уровень олицетворения не назначается. <xref:System.Security.Principal.TokenImpersonationLevel> указывает, что серверный процесс не может получать идентификационную информацию о клиенте и олицетворять клиента. <xref:System.Security.Principal.TokenImpersonationLevel> указывает, что процесс сервера может получать информацию о клиенте, например идентификаторы и привилегии безопасности, но не может олицетворять клиента. Это может оказаться полезным в том случае, если сервер экспортирует свои собственные объекты, например базы данных, из которых экспортируются таблицы и представления. Используя полученную информацию безопасности клиента, сервер может принимать решения в отношении проверки доступа, не имея возможности применять другие службы, использующие контекст безопасности клиента. <xref:System.Security.Principal.TokenImpersonationLevel> указывает, что процесс сервера может олицетворять контекст безопасности клиента в своей локальной системе. Олицетворение клиента сервером в удаленных системах невозможно. <xref:System.Security.Principal.TokenImpersonationLevel> указывает, что процесс сервера может олицетворять контекст безопасности клиента в удаленных системах.|
|<xref:System.ServiceModel.Activities.Send.Endpoint%2A>||<xref:System.ServiceModel.Endpoint>, которому действие <xref:System.ServiceModel.Activities.Send> отправляет сообщение. Если это свойство имеет значение <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> свойство должно иметь значение **null**.|
|<xref:System.ServiceModel.Activities.Send.EndpointAddress%2A>||<xref:System.ServiceModel.EndpointAddress>, которому направляется сообщение.|
|<xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A>||Имя конфигурации конечной точки. Это свойство задается при настройке конечной точки в файле конфигурации. Это свойство должно быть присвоено имя, заданное  **\<endpoint >** элемент в файле конфигурации. Если это свойство задано, <xref:System.ServiceModel.Activities.Send.Endpoint%2A> свойство должно иметь значение **null**.|

## <a name="see-also"></a>См. также

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)