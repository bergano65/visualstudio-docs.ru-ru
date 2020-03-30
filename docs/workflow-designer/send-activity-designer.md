---
title: Дизайнер рабочего процесса - Отправить деятельности дизайнер
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8690d5ccf18c752aacb37a71243d9f591fb9ee30
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395224"
---
# <a name="send-activity-designer"></a>Конструктор действия Send

Для создания и настройки <xref:System.ServiceModel.Activities.Send> действия используется разработчик активности **Send.**

## <a name="the-send-activity"></a>Действие Send

 Действие <xref:System.ServiceModel.Activities.Send> предназначено для отправки сообщения службе. Действие <xref:System.ServiceModel.Activities.ReceiveReply> может быть привязано к действию <xref:System.ServiceModel.Activities.Send>, которое получает сообщение в процессе обмена сообщениями по шаблону «запрос-ответ» на стороне клиента.

### <a name="using-the-send-activity-designer"></a>Использование конструктора действия Send

Доступ к разработчику активности **Отправки** в категории **«Сообщения»** **в Наборе инструментов.** Конструктор активности **Отправки** может быть перевезен из **панели инструментов** и сброшен на поверхность рабочего процесса Designer везде, где обычно размещаются действия. Будет создано действие <xref:System.ServiceModel.Activities.Send> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> Send. Можно <xref:System.Activities.Activity.DisplayName%2A> редактировать в заголовке дизайнера деятельности **Отправить** или в поле **DisplayName** сетки свойств.

Чтобы создать <xref:System.ServiceModel.Activities.ReceiveReply> действие и привязать <xref:System.ServiceModel.Activities.Send> его к выбранной деятельности, нажмите правой кнопкой **Кнопка Отправить** деятельности дизайнера, нажмите **На создание ReceiveReply** пункт в контекстном меню и **ReceiveReplyForSend** дизайнер появляется ниже **отправить** дизайнера. Действие <xref:System.ServiceModel.Activities.ReceiveReply> получает сообщение в процессе обмена сообщениями по шаблону «запрос-ответ» на стороне клиента. Он может быть настроен с помощью дизайнера **ReceiveReplyForSend.**

Кроме того, конструктор шаблона **SendAndReceiveReply** в категории **«Сообщения»** **Toolbox** может быть <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> использован для создания пары предварительно настроенных и действий. Для получения дополнительной информации об использовании шаблонов **SendAndReceiveReply** [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) и **ReceiveReplyForSend** см.

### <a name="the-send-activity-properties"></a>Свойства действия Send

В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.Send> и описано их использование в конструкторе. Эти свойства можно редактировать в сетке свойств или на поверхности рабочего процесса Designer.

| Имя свойства | Обязательно | Использование |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Понятное имя действия <xref:System.ServiceModel.Activities.Send>. Значение по умолчанию - Send. Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | True | Имя операции службы, вызываемой этим действием <xref:System.ServiceModel.Activities.Send>. Это свойство используется для построения значения по умолчанию для свойства **действия,** если свойство **действия** явно не установлено. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | True | Имя контракта службы, который реализуется вызываемой службой. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | False | Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Отспособьте это свойство, выбрав кнопку ellipsis рядом с полем **содержимого** в сетке свойств или нажав кнопку **Define...** рядом с меткой **Content** на поверхности дизайнера активности **Receive.** Оба отображения диалог **определения содержимого.** Для получения дополнительной информации о том, как использовать это поле, см. [Content Definition Dialog Box](../workflow-designer/content-definition-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | False | Задает метод <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для перенаправления сообщения в соответствующий экземпляр рабочего процесса.<br /><br /> Нажмите кнопку ellipsis <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> рядом с свойством в сетке свойств, чтобы открыть диалоговую будку **expression Editor.** Для получения дополнительной информации об использовании [How to: Use the Expression Editor](../workflow-designer/how-to-use-the-expression-editor.md) этого диалогового окна см. |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | False | Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Send> в рамках рабочего процесса. Нажмите кнопку ellipsis <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> рядом с свойством в сетке свойств, чтобы открыть диалоговую коробку **Add Correlation Initialis.** Для получения дополнительной информации об использовании этого окна, [см.](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | False | Коллекция известных типов для операции службы, вызываемой этим действием <xref:System.ServiceModel.Activities.Send>. Это свойство должно использоваться вместе со свойством <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>, установленным в значение <xref:System.Runtime.Serialization.DataContractSerializer>. Не учитывается, если используется <xref:System.Xml.Serialization.XmlSerializer>.<br /><br /> Выберите кнопку ellipsis рядом с полем **KnownTypes** в сетке свойств, чтобы отобразить диалог **редактора типсбора,** с помощью которого можно добавить соответствующие типы.<br /><br /> Выберите кнопку ellipsis рядом с полем **KnownTypes** в сетке свойств, чтобы отобразить диалоговое окно **редактора типа,** с помощью которого можно добавить соответствующие типы. Для получения дополнительной информации об [использовании](../workflow-designer/type-collection-editor-dialog-box.md) этого окна, см. |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | True | Задает <xref:System.Net.Security.ProtectionLevel> для сообщения.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> означает только аутентификацию.<br />2. <xref:System.Net.Security.ProtectionLevel> означает знак данных, чтобы помочь обеспечить целостность передаваемых данных.<br />3. <xref:System.Net.Security.ProtectionLevel> означает шифрование и подписание данных, чтобы помочь обеспечить конфиденциальность и целостность передаваемых данных. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | True | Сериализатор, используемый для этой операции службы, вызываемой действием <xref:System.ServiceModel.Activities.Send>. Значение по умолчанию - <xref:System.Runtime.Serialization.DataContractSerializer>, при котором производится сериализация и десериализация экземпляра типа в XML-поток или документ с использованием переданного контракта данных. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | False | Указывает заголовок действия сообщения. Если он явно не установлен, его значение `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`по умолчанию: . Если задано для действия <xref:System.ServiceModel.Activities.Send>, то для успешной доставки сообщения действие <xref:System.ServiceModel.Activities.Receive>, принимающее сообщение, должно иметь то же значение. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | <xref:System.Security.Principal.TokenImpersonationLevel>, допустимое для получателя сообщения. Он определяет уровни олицетворения безопасности, которые определяют степень, в которой серверный процесс может действовать от имени клиентского процесса.<xref:System.Security.Principal.TokenImpersonationLevel>  указывает, что уровень олицетворения не назначается. <xref:System.Security.Principal.TokenImpersonationLevel>указывает на то, что серверный процесс не может получить идентификационную информацию о клиенте и не может выдавать себя за клиента. <xref:System.Security.Principal.TokenImpersonationLevel>указывает на то, что серверный процесс может получить информацию о клиенте, такую как идентификаторы безопасности и привилегии, но что он не может выдавать себя за клиента. Это может оказаться полезным в том случае, если сервер экспортирует свои собственные объекты, например базы данных, из которых экспортируются таблицы и представления. Используя полученную информацию безопасности клиента, сервер может принимать решения в отношении проверки доступа, не имея возможности применять другие службы, использующие контекст безопасности клиента. <xref:System.Security.Principal.TokenImpersonationLevel>указывает на то, что процесс сервера может выдавать себя за контекст безопасности клиента в локальной системе. Олицетворение клиента сервером в удаленных системах невозможно. <xref:System.Security.Principal.TokenImpersonationLevel>указывает на то, что процесс сервера может выдавать себя за контекст безопасности клиента на удаленных системах. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | <xref:System.ServiceModel.Endpoint>, которому действие <xref:System.ServiceModel.Activities.Send> отправляет сообщение. Если это свойство <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> установлено, свойство должно быть **нулевым.** |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | <xref:System.ServiceModel.EndpointAddress>, которому направляется сообщение. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Имя конфигурации конечной точки. Это свойство задается при настройке конечной точки в файле конфигурации. Это свойство должно быть установлено на имя, данное в ** \<элементе>в** файле конфигурации. Если это свойство <xref:System.ServiceModel.Activities.Send.Endpoint%2A> установлено, свойство должно быть **нулевым.** |

## <a name="see-also"></a>См. также

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Получить](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)