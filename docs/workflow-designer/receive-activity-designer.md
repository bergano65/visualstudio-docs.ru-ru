---
title: Конструктор действий получения конструктор рабочих процессов
description: Сведения о действии Receive и об использовании конструктора действий получения для создания и настройки действия Receive.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ceff7d40ffd0d7c961f07dd65a8070a8f11a1b4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899379"
---
# <a name="receive-activity-designer"></a>Конструктор действия Receive

Конструктор действия **Receive** используется для создания и настройки <xref:System.ServiceModel.Activities.Receive> действия. Действие <xref:System.ServiceModel.Activities.Receive> получает сообщение - либо встроенное, например <xref:System.ServiceModel.Channels.Message>, <xref:System.IO.Stream> или <xref:System.Xml.Linq.XElement>, либо определяемое контрактом данных приложения, контрактом сообщений или классом XML, поддерживающим сериализацию.

## <a name="the-receive-activity"></a>Действие Receive

Действие <xref:System.ServiceModel.Activities.Receive> может получать один или несколько элементов в зависимости от используемого типа приема содержимого. Действие <xref:System.ServiceModel.Activities.SendReply> может быть привязано к действию <xref:System.ServiceModel.Activities.Receive>, которое получает сообщение в процессе обмена сообщениями по шаблону «запрос-ответ» на стороне службы.

### <a name="using-the-receive-activity-designer"></a>Использование конструктора действия Receive

Доступ к конструктору действий **получения** в категории **обмена сообщениями** **панели элементов**. Конструктор операций **получения** можно перетащить из **панели элементов** в конструктор рабочих процессов область, где обычно размещаются действия. При этом создается действие <xref:System.ServiceModel.Activities.Receive> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Receive. <xref:System.Activities.Activity.DisplayName%2A>Можно изменить в заголовке конструктора действий **получения** или в поле **DisplayName** сетки свойств.

Чтобы создать <xref:System.ServiceModel.Activities.SendReply> действие и привязать его к выбранному <xref:System.ServiceModel.Activities.Receive> действию, щелкните правой кнопкой мыши конструктор действий **получения** , щелкните элемент **Создать SendReply** в контекстном меню, и конструктор **SendReplyToReceive** появится под конструктором **получения** . Действие <xref:System.ServiceModel.Activities.SendReply> отправляет ответное сообщение в процессе обмена сообщениями по шаблону «запрос-ответ» на стороне службы. Его можно настроить с помощью конструктора **SendReplyToReceive** .

Кроме того, конструктор шаблонов **ReceiveAndSendReply** в категории **сообщений** **панели элементов** можно использовать для создания пары предварительно настроенных <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply> действий. Дополнительные сведения об использовании шаблона **ReceiveAndSendReply** и **SendReplyToReceive** см. в разделе [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) .

### <a name="the-receive-activity-properties"></a>Свойства действия Receive

В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.Receive> и описано их использование в конструкторе. Эти свойства можно изменять в сетке свойств или на поверхности конструктор рабочих процессов. Свойство <xref:System.ServiceModel.Activities.Receive.OperationName%2A> является единственным обязательным свойством.

| Имя свойства | Обязательно | Использование |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Указывает понятное имя действия <xref:System.ServiceModel.Activities.Receive>. Значение по умолчанию - Receive.<br /><br /> Несмотря на то, что использовать значение, отличное от значения по умолчанию, для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не требуется, его все же рекомендуется использовать. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | True | Указывает имя операции службы, реализуемой этим действием <xref:System.ServiceModel.Activities.Receive>. Это свойство используется для создания значения по умолчанию для свойства **Action** , если свойство **Action** не задано явно. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | False | Задает имя контракта службы. Данное свойство используется для группирования операций служб в отдельные контракты служб. Все действия <xref:System.ServiceModel.Activities.Receive>, которые имеют одинаковое имя контракта <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>, группируются по этому контракту службы (тип порта WSDL). Значение по умолчанию — полное имя CLR для действия верхнего уровня (корневого). |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | False | Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Измените это свойство, нажав кнопку с многоточием рядом с полем **содержимое** в сетке свойств или нажав кнопку **определить...** рядом с меткой **содержимого** в области конструктора действий **получения** . В обоих окнах отображается диалоговое окно **определения содержимого** . Дополнительные сведения об использовании этого поля см. в разделе [диалогового окна «Определение содержимого](../workflow-designer/content-definition-dialog-box.md) ». |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | False | Указывает корреляции между действиями <xref:System.ServiceModel.Activities.Receive> в операциях службы рабочего процесса с объектом <xref:System.ServiceModel.MessageQuerySet>. Нажмите кнопку с многоточием рядом со <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> свойством в сетке свойства, чтобы открыть диалоговое окно **Определение CorrelatesOn** . Дополнительные сведения об использовании этого диалогового окна см. в разделе [диалогового окна «Определение содержимого](../workflow-designer/content-definition-dialog-box.md) ». |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | False | Задает метод <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для перенаправления сообщения в соответствующий экземпляр рабочего процесса.<br /><br /> Нажмите кнопку с многоточием рядом со <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> свойством в сетке свойства, чтобы открыть диалоговое окно **Редактор выражений** . Дополнительные сведения об использовании этого диалогового окна см. в разделе [инструкции. Использование редактора выражений](../workflow-designer/how-to-use-the-expression-editor.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | False | Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса. Нажмите кнопку с многоточием рядом со <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> свойством в сетке свойства, чтобы открыть диалоговое окно **Добавление инициализаторов корреляции** . Дополнительные сведения об использовании этого поля см. в разделе « [Добавление CorrelationInitializers в диалоговом окне](../workflow-designer/add-correlationinitializers-dialog-box.md) ». |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | False | Указывает значение, которое определяет, может ли быть создан новый экземпляр рабочего процесса для обработки сообщения в случае, если сообщение не соответствует существующему экземпляру рабочего процесса. Если значение равно **true**, создается новый экземпляр рабочего процесса для обработки сообщения, если сообщение не сопоставлено с существующим экземпляром рабочего процесса. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | False | Указывает коллекцию известных типов для операции службы, реализуемой этим действием <xref:System.ServiceModel.Activities.Receive>. Это свойство должно использоваться вместе со свойством <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>, установленным в значение <xref:System.Runtime.Serialization.DataContractSerializer>. Не учитывается, если используется <xref:System.Xml.Serialization.XmlSerializer>.<br /><br /> Нажмите кнопку с многоточием рядом с полем **кновнтипес** в сетке свойств, чтобы открыть диалоговое окно **Редактор коллекции типов** , в котором можно добавить соответствующие типы. Дополнительные сведения об использовании этого поля см. в разделе [диалогового окна Редактор коллекции типов](../workflow-designer/type-collection-editor-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | False | Задает <xref:System.Net.Security.ProtectionLevel> для сообщения.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> обозначает только проверку подлинности.<br />2.  <xref:System.Net.Security.ProtectionLevel> означает подписывание данных для обеспечения целостности передаваемых данных.<br />3.  <xref:System.Net.Security.ProtectionLevel> означает шифрование и подписывание данных для обеспечения конфиденциальности и целостности передаваемых данных. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | False | Указывает тип используемого сериализатора для операции службы, реализуемой действием <xref:System.ServiceModel.Activities.Receive>. Значение по умолчанию равно <xref:System.Runtime.Serialization.DataContractSerializer>, при котором выполняется сериализация и десериализация экземпляра типа в XML-поток или документ, который использует переданный контракт данных. <xref:System.Xml.Serialization.XmlSerializer> также может быть использован в том случае, если необходим больший контроль над XML. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | False | Указывает заголовок действия сообщения. Если параметр не задан явно, его значение по умолчанию равно: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . |

## <a name="see-also"></a>См. также раздел

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Отправить](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
