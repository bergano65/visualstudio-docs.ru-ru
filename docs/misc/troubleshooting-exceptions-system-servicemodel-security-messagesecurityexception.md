---
title: "Разрешение вопросов, связанных с исключениями: System.ServiceModel.Security.MessageSecurityException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.ServiceModel.Security.MessageSecurityException - исключение"
  - "MessageSecurityException - исключение"
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.ServiceModel.Security.MessageSecurityException
Исключение <xref:System.ServiceModel.Security.MessageSecurityException> вызывается, когда [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] определяет, что сообщение не защищено правильно или было фальсифицировано. Эта ошибка возникает чаще всего, если выполняются все следующие условия:  
  
-   Для связи веб–узла или проекта веб–приложения со службой WCF \(.svc\) используется ссылка на службу WCF через удаленное подключение, такое как подключение к удаленному рабочему столу или службы терминалов.  
  
-   У вас нет прав администратора на удаленном веб–узле.  
  
-   Запросы к localhost на удаленном веб–узле обрабатываются [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server.  
  
## Полезные советы  
 **Устраните проблемы с проверкой подлинности NTLM при использовании ASP.NET Development Server.**  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server обычно отключает безопасность Windows NT Challenge\/Response \(NTLM\), что разрешает анонимный доступ. По умолчанию при выполнении сеанса служб терминалов или использовании удаленного подключения безопасность NTLM включена. Когда NTLM включена, все запросы к localhost проверяются по учетным данным пользователя или процесса, запустившего [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server. Это снижает угрозу безопасности. Однако WCF также выполняет собственную проверку подлинности и не разрешает учетной записи, не относящейся к администраторам, пользоваться службами WCF.  
  
 Если удаленный пользователь может запустить веб–узел с помощью [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server, а также работать с веб–службой или службой WCF, можно создать пользовательскую привязку службы или отключить безопасность NTLM.  
  
> [!IMPORTANT]
>  Не рекомендуется отключать безопасность NTLM. Это может представлять угрозу безопасности.  
  
 При создании пользовательской привязки службы по–прежнему выполняется защита с помощью проверки подлинности NTLM.  
  
 Выполните следующие действия для создания пользовательской службы привязки для службы WCF.  
  
#### Чтобы создать пользовательскую привязку службы для службы WCF, работающей под ASP.NET Development Server  
  
1.  Откройте файл Web.config для службы WCF, которая вызывает исключение.  
  
2.  Введите следующую информацию в файл Web.config.  
  
    ```  
    <bindings> <customBinding> <binding name="Service1Binding"> <transactionFlow /> <textMessageEncoding /> <httpTransport authenticationScheme="Ntlm" /> </binding> </customBinding> </bindings>  
    ```  
  
3.  Сохраните изменения и закройте файл Web.config.  
  
4.  В коде WCF или веб–службы измените значение конечной точки на следующее:  
  
    ```  
    <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />  
    ```  
  
     Это гарантирует, что служба использует пользовательскую привязку.  
  
5.  Добавьте ссылку на эту службу в веб–приложение, которое обращается к службе. \(В диалоговом окне **Добавить ссылку на службу** добавьте ссылку на службу, так же как для исходной службы, которая создавала исключения.\)  
  
 Выполните следующие действия для отключения безопасности NTLM при работе со ссылкой на службу WCF.  
  
> [!IMPORTANT]
>  Не рекомендуется отключать безопасность NTLM. Это может представлять угрозу безопасности.  
  
#### Чтобы отключить безопасность NTLM  
  
1.  В **Обозревателе решений** щелкните правой кнопкой мыши имя веб–узла, затем **Страницы свойств**.  
  
2.  Выберите пункт **Параметры запуска**, а затем снимите флажок **Проверка подлинности NTLM**.  
  
3.  Нажмите кнопку **ОК**.  
  
## См. также  
 <xref:System.ServiceModel.Security.MessageSecurityException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)