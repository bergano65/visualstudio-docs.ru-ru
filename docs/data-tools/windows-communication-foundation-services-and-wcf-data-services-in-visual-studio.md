---
title: "Служб Windows Communication Foundation и службы данных WCF в Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: b73e2cf93cf0f557db072586b7aa67ab730fad4f
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Службы Windows Communication Foundation и службы данных WCF в Visual Studio
Visual Studio предоставляет средства для работы с Windows Communication Foundation (WCF) и [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], технологии Microsoft для создания распределенных приложений. В этом разделе содержатся вводные службы от [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] перспективы. Полную документацию см. в разделе [служб данных WCF 4.5](/dotnet/framework/data/wcf/index).  
  
## <a name="what-is-wcf"></a>Что такое WCF  
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]— Это единое платформа для создания распределенных приложений безопасную, надежную, транзакций и с возможностью взаимодействия. Он заменяет старую межпроцессного взаимодействия технологий, таких как службы ASMX Web, удаленное взаимодействие .NET, Enterprise Services (DCOM) и MSMQ. WCF объединяет в себе функциональные возможности всех этих технологий в унифицированную модель программирования. Это упрощает процесс разработки распределенных приложений.  
  
#### <a name="what-are-wcf-data-services"></a>Что такое службы данных WCF  
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]Реализация протокола Open Data (OData) является стандартным.  Службы данных WCF позволяет предоставляют табличные данные в виде набора интерфейсов API REST, что позволяет возвращать данные с помощью стандартных команд HTTP, такие как GET, POST, PUT или DELETE. На стороне сервера службы данных WCF заменяемые [веб-API ASP.NET](http://www.asp.net/web-api) для создания новых служб OData. Клиентская библиотека служб данных WCF по-прежнему будет хорошим выбором для работы со службами OData в приложении .NET из Visual Studio (**проекта &#124; Добавление ссылки на службу**). Дополнительные сведения см. в разделе [служб данных WCF 4.5](http://go.microsoft.com/fwlink/?LinkID=119952).  
  
### <a name="wcf-programming-model"></a>Модель программирования WCF  
 Модель программирования WCF основана на связи между двумя сущностями: служба WCF и клиент WCF. Модель программирования, содержащийся в <xref:System.ServiceModel> пространства имен в [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
#### <a name="wcf-service"></a>Служба WCF  
 Служба WCF основана на интерфейс, определяющий контракт между службой и клиентом. Он помечен с помощью <xref:System.ServiceModel.ServiceContractAttribute> атрибута, как показано в следующем коде:  
  
 [!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]  
  
 [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]  
  
 Определение функции или методы, предоставляемые службой WCF, помечая их с <xref:System.ServiceModel.OperationContractAttribute> атрибута. Кроме того, можно предоставить сериализованные данные, пометив составной тип <xref:System.Runtime.Serialization.DataContractAttribute> атрибута. Это позволяет привязывать данные в клиенте.  
  
 После определения интерфейса и его методы они инкапсулируются в класс, реализующий интерфейс. Один класс службы WCF можно реализовать несколько контрактов службы.  
  
 Служба WCF предоставляется для использования посредством что называется *конечная точка*. Конечная точка содержит единственный способ взаимодействия со службой; не удается доступа к службе через прямые ссылки, как и с другими классами.  
  
 Конечная точка состоит из адреса, привязки и контракта. Определяет адрес, где расположена служба; Это может быть URL-адрес, адрес FTP или сетевой или локальный путь. Привязка определяет способ обмена данными со службой. Привязки WCF предоставляют гибкую модель для задания протокола, например HTTP или FTP, механизма обеспечения безопасности, такие как проверка подлинности Windows или имена пользователей и пароли и многое другое. Контракт включает операции, предоставляемые классом службы WCF.  
  
 Для одной службы WCF может быть представлено несколько конечных точек. Это позволяет разным клиентам взаимодействовать с той же службы по-разному. Например банковская служба может предоставить одну конечную точку для сотрудников, а другая — для внешних клиентов, использующих разные адреса, привязки, и/или контракта.  
  
#### <a name="wcf-client"></a>Клиент WCF  
 Клиент WCF состоит из *прокси-сервера* , позволяет приложению взаимодействовать со службой WCF и конечной точки, соответствующей конечной точке, заданной для этой службы. Прокси-сервер создается на стороне клиента в файле app.config и включает сведения о типах и методы, предоставляемые службой. Для служб, предоставляющих несколько конечных точек клиент может выбрать ту, которая наилучшим образом соответствует потребностям, например, для взаимодействия по протоколу HTTP и использовать проверку подлинности Windows.  
  
 После создания клиента WCF можно ссылаться на службу в коде так же, как и любой другой объект. Например, чтобы вызвать `GetData` метода, показанного выше, можно написать код, который имеет следующий вид:  
  
 [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]  
  
## <a name="wcf-tools-in-visual-studio"></a>Средства служб WCF в Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]предоставляет средства для создания служб WCF и клиенты WCF. Пошаговое руководство, демонстрирующее эти средства, в разделе [Пошаговое руководство: создание простой службы WCF в Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).  
  
### <a name="creating-and-testing-wcf-services"></a>Создание и тестирование службы WCF  
 Можно использовать WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] шаблоны как основу для быстрого создания собственной службы. Затем можно использовать WCF Service Auto Host и тестовый клиент WCF для отладки и тестирования службы. Вместе эти средства обеспечивают быстрый и удобный цикл отладки и тестирования и исключает необходимость фиксации модели размещения на ранней стадии.  
  
#### <a name="wcf-templates"></a>Шаблоны WCF  
 WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] шаблонов предоставляют базовую структуру класса для разработки службы. Имеется несколько шаблонов WCF в **Добавление нового проекта** диалоговое окно. К ним относятся проекты библиотеки служб WCF, веб-сайтов службы WCF и шаблонов элементов службы WCF.  
  
 При выборе шаблона файлы добавляются в контракт службы, реализации службы и конфигурации службы. Все необходимые атрибуты уже добавлена, создания простого типа «Hello World», службы, а не содержал написания кода. Конечно, необходимо добавить код для обеспечения функций и методов реальной службы, но шаблоны обеспечивают основу.  
  
 Дополнительные сведения о шаблонах WCF см. в разделе [шаблоны WCF в Visual Studio](/dotnet/framework/wcf/wcf-vs-templates).  
  
#### <a name="wcf-service-host"></a>Узел службы WCF  
 При запуске [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] отладчика (нажатием клавиши F5) для проекта службы WCF, узла службы WCF, автоматически запускается инструмент для размещения этой службы локально. Узел службы WCF выполняет перечисление служб в проекте службы WCF, загружает конфигурацию проекта и создает экземпляр узла для каждой найденной службы.  
  
 Используя узел службы WCF, для тестирования службы WCF без создания дополнительного кода или фиксации в конкретном узле во время разработки.  
  
 Дополнительные сведения об узле службы WCF см. в разделе [узел службы WCF (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).  
  
#### <a name="wcf-test-client"></a>Тестовый клиент WCF  
 Тестовый клиент WCF средство позволяет вводить тестовые параметры, отправить их в службу WCF и просмотреть ответ, то служба отправляет обратно. Он обеспечивает удобную практику тестирования при их сочетании с узлом службы WCF службы. Это средство можно найти в папке \Common7\IDE, в которой для Visual Studio 2015 установлен на диске C: в данном случае: **C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\IDE\\**.  
  
 При нажатии клавиши F5 для отладки проекта службы WCF, тестовый клиент WCF открывает и отображает список конечных точек службы, которые определены в файле конфигурации. Можно протестировать эти параметры и запустить службу и повторять этот процесс для последовательного тестирования и проверки службы.  
  
 Дополнительные сведения о тестовом клиенте WCF см. в разделе [тестовый клиент WCF (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).  
  
### <a name="accessing-wcf-services-in-visual-studio"></a>Доступ к службам WCF в Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]упрощает задачу создания клиентов WCF, автоматически создавая прокси и конечную точку для службы, добавленные с помощью **добавить ссылку на службу** диалоговое окно. Все необходимые сведения о конфигурации добавляется в файл app.config. Большая часть времени, все, что нужно сделать — это создать службу для использования в.  
  
 **Добавить ссылку на службу** диалоговое окно позволяет вводить адрес службы или для поиска службы, определенные в решении. Диалоговое окно возвращает список служб и операций, предоставляемых этими службами. Он также позволяет определить пространство имен, по которому будут приведены ссылки на службы в коде.  
  
 **Настройка ссылок на службы** диалоговое окно позволяет настроить конфигурацию службы. Можно изменить адрес службы, задать уровень доступа, асинхронное поведение и типы контрактов сообщений и настроить повторное использование типов.  
  
## <a name="how-to-select-a-service-endpoint"></a>Как: выберите конечную точку службы  
Некоторые службы Windows Communication Foundation (WCF) выдать несколько конечных точек, через которые клиент может связаться со службой. Например, служба может предоставлять одну конечную точку, использующую HTTP привязки и имя пользователя и пароля и вторую конечную точку, использующую FTP и проверку подлинности Windows. Первая конечная точка может использоваться приложениями, которые обращаются к службе с внешней стороны брандмауэра, в то время как второй может использоваться во внутренней сети.  
  
В этом случае можно указать `endpointConfigurationName` в качестве параметра конструктора для ссылки на службу.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-select-a-service-endpoint"></a>Чтобы выбрать конечную точку службы  
  
1.  Добавьте ссылку на службу WCF, щелкнув правой кнопкой мыши узел проекта в обозревателе решений и выбрав **Добавление ссылки на службу**.
  
2.  В редакторе кода добавьте конструктор для ссылки на службу:  
  
    ```vb  
    Dim proxy As New ServiceReference.Service1Client(  
    ```  
  
    ```csharp  
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(  
    ```  
  
    > [!NOTE]
    >  Замените *ServiceReference* с пространством имен для ссылки на службу и замены *Service1Client* с именем службы.  
  
3.  Список IntelliSense отображается с помощью перегрузок для конструктора. Выберите `endpointConfigurationName As String` перегрузки.  
  
4.  Перегрузке, введите `=` *ConfigurationName*, где *ConfigurationName* имя конечной точки, которую вы хотите использовать.  
  
    > [!NOTE]
    >  Если вы не знаете имена доступных конечных точек, их можно найти в файле app.config.  
  
#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Чтобы найти доступные конечные точки для службы WCF  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши файл app.config проекта, содержащего ссылку на службу и нажмите кнопку **откройте**. Файл появится в редакторе кода.  
  
2.  Поиск `<Client>` тег в файле.  
  
3.  Поиск под `<Client>` тег для тега, который начинается с `<Endpoint>`.  
  
     Если ссылка на службу предоставляет несколько конечных точек, будет существовать две или более `<Endpoint` тегов.  
  
4.  Внутри `<EndPoint>` тег можно найти `name="` *SomeService* `"` параметра (где *SomeService* представляет имя конечной точки). Это имя для конечной точки, которая может быть передан `endpointConfigurationName As String` перегрузки конструктора для ссылки на службу.  
  
## <a name="how-to-call-a-service-method-asynchronously"></a>Как: асинхронный вызов метода службы  
Большинство методов в службах Windows Communication Foundation (WCF) могут вызываться синхронно или асинхронно. Асинхронный вызов метода позволяет приложению продолжать работу при вызове метода через медленное подключение.  
  
По умолчанию при добавлении ссылки на службу в проект он настраивается для вызова методов синхронно. Можно изменить поведение для асинхронного вызова методов, изменив параметр в **настроить ссылку на службу** диалоговое окно.  
  
> [!NOTE]
>  Этот параметр устанавливается отдельно для каждой службы. Если один метод для службы вызывается асинхронно, все методы должны вызываться асинхронно.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-call-a-service-method-asynchronously"></a>Асинхронный вызов метода службы  
  
1.  В **обозревателе решений**, выберите ссылку на службу.  
  
2.  На **проекта** меню, нажмите кнопку **настроить ссылку на службу**.  
  
3.  В **настроить ссылку на службу** выберите **создать асинхронные операции** флажок.  
  
## <a name="how-to-bind-data-returned-by-a-service"></a>Как: привязки данных, возвращенных службой,  
Можно привязать данные, возвращаемые службой Windows Communication Foundation (WCF) для элемента управления так же, как любой другой источник данных можно привязать к элементу управления. При добавлении ссылки на службу WCF, если служба содержит составные типы, которые возвращают данные, они автоматически добавляются к **источники данных** окна.  
  
#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Чтобы привязать элемент управления к одному полю данных возвращаемого службой WCF  
  
1.  В меню **Данные** выберите команду **Показать источники данных**. **Источники данных** появится окно.  
  
2.  В **источники данных** окна, разверните узел для ссылки на службу. Отображаются все составные типы, возвращенных службой.  
  
3.  Разверните узел для типа. Поля данных для этого типа будут отображаться.  
  
4.  Выберите поле и щелкните стрелку раскрывающегося списка для отображения списка элементов управления, которые доступны для типа данных.  
  
5.  Выберите тип элемента управления, который требуется привязать.  
  
6.  Перетащите поле на форму. Элемент управления будет добавлен в форму вместе с <xref:System.Windows.Forms.BindingSource> компонента и <xref:System.Windows.Forms.BindingNavigator> компонента.  
  
7.  Повторите шаги 4 6 для любых других полей, необходимо выполнить привязку.  
  
#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Чтобы привязать элемент управления к составному типу, возвращаемому службой WCF  
  
1.  На **данные** последовательно выберите пункты **Показать источники данных**. **Источники данных** появится окно.  
  
2.  В **источники данных** окна, разверните узел для ссылки на службу. Отображаются все составные типы, возвращенных службой.  
  
3.  Выберите узел типа и щелкните стрелку раскрывающегося списка, чтобы отобразить список доступных параметров.  
  
4.  Выберите либо **DataGridView** для отображения данных в виде сетки или **сведения** для отображения данных в отдельных элементах управления.  
  
5.  Перетащите узел в форме. Элементы управления будут добавлены в форму вместе с <xref:System.Windows.Forms.BindingSource> компонента и <xref:System.Windows.Forms.BindingNavigator> компонента.  
  
## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Как: Настройка службы для повторного использования существующих типов  
При добавлении в проект ссылки на службу в локальном проекте создаются все типы, заданные в службе. В большинстве случаев создаются дублирующиеся типы Если служба использует Общие [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] типы или типы заданы в общей библиотеке.  
  
Чтобы избежать этой проблемы, по умолчанию общим типы в сборках, на которую указывает ссылка. Если вы хотите отключить совместное использование типов для одной или нескольких сборок, это можно выполнить в **Настройка ссылок на службы** диалоговое окно.  
  
#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Чтобы отключить совместное использование типов в одной сборке  
  
1.  В **обозревателе решений**, выберите ссылку на службу.  
  
2.  На **проекта** меню, нажмите кнопку **настроить ссылку на службу**.  
  
3.  В **Настройка ссылок на службы** выберите **повторно использовать типы в указанных сборках, на которую указывает ссылка**.  
  
4.  Установите флажок для каждой сборки, в которой вы хотите включить совместное использование типов. Чтобы отключить совместное использование типов для сборки, оставьте флажок снятым.  
  
#### <a name="to-disable-type-sharing-in-all-assemblies"></a>Чтобы отключить совместное использование типов в все сборки  
  
1.  В **обозревателе решений**, выберите ссылку на службу.  
  
2.  На **проекта** меню, нажмите кнопку **настроить ссылку на службу**.  
  
3.  В **Настройка ссылок на службы** снимите флажок **повторно использовать типы в указанных сборках** флажок.  
  
## <a name="related-topics"></a>Связанные разделы  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Пошаговое руководство. Создание простой службы WCF в Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Пошаговая демонстрация создания и использования служб WCF в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Пошаговое руководство. Создание службы данных WCF с помощью WPF и Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Пошаговая демонстрация того, как создавать и использовать [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Использование средств разработки WCF](/dotnet/framework/wcf/using-the-wcf-development-tools)|Объясняет способы создания и тестирования служб WCF в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
||[Практическое руководство. Добавление, обновление или удаление ссылки на службу данных WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Описывает, как использовать [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Диагностика ссылок на службы](../data-tools/troubleshooting-service-references.md)|Представляет некоторые распространенные ошибки, которые могут возникать с ссылки на службу и способов их устранения.|  
|[Отладка служб WCF](../debugger/debugging-wcf-services.md)|Описание общих проблем отладки и методов, которыми можно столкнуться при отладке службы WCF.|  
|[Пошаговое руководство. Создание многоуровневого приложения для работы с данными](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Содержит пошаговые инструкции по созданию типизированного набора данных и разделения кода адаптера таблицы и набора данных на несколько проектов.|  
|[Диалоговое окно "Настроить ссылку на службу"](../data-tools/configure-service-reference-dialog-box.md)|Описание элементов пользовательского интерфейса из **настроить ссылку на службу** диалоговое окно.|  
  
## <a name="reference"></a>Ссылка  
 <xref:System.ServiceModel>  
  
 <xref:System.Data.Services>  
  
## <a name="see-also"></a>См. также  
 [Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)