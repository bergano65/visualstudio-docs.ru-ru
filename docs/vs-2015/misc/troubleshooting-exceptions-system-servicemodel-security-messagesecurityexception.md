---
title: 'Устранение исключений: System.ServiceModel.Security.MessageSecurityException | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: troubleshooting
helpviewer_keywords:
- System.ServiceModel.Security.MessageSecurityException exception
- MessageSecurityException exception
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b6d63393313097503ed92c8a540d85152b3f8688
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993253"
---
# <a name="troubleshooting-exceptions-systemservicemodelsecuritymessagesecurityexception"></a>Устранение исключений: System.ServiceModel.Security.MessageSecurityException
Объект <xref:System.ServiceModel.Security.MessageSecurityException> исключение создается, когда [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] определяет, что сообщение не защищено правильно или было изменено. Эта ошибка возникает чаще всего, если выполняются все следующие условия:  
  
-   Для связи веб–узла или проекта веб–приложения со службой WCF (.svc) используется ссылка на службу WCF через удаленное подключение, такое как подключение к удаленному рабочему столу или службы терминалов.  
  
-   У вас нет прав администратора на удаленном веб–узле.  
  
-   Запросы к localhost на удаленном веб–узле обрабатываются [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server.  
  
## <a name="associated-tips"></a>Полезные советы  
 **Устранение проблем с проверкой подлинности NTLM при использовании ASP.Net Development Server.**  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server обычно отключает безопасность Windows NT Challenge/Response (NTLM), что разрешает анонимный доступ. По умолчанию при выполнении сеанса служб терминалов или использовании удаленного подключения безопасность NTLM включена. Когда NTLM включена, все запросы к localhost проверяются по учетным данным пользователя или процесса, запустившего [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server. Это снижает угрозу безопасности. Однако WCF также выполняет собственную проверку подлинности и не разрешает учетной записи, не относящейся к администраторам, пользоваться службами WCF.  
  
 Если удаленный пользователь может запустить веб–узел с помощью [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server, а также работать с веб–службой или службой WCF, можно создать пользовательскую привязку службы или отключить безопасность NTLM.  
  
> [!IMPORTANT]
>  Не рекомендуется отключать безопасность NTLM. Это может представлять угрозу безопасности.  
  
 При создании пользовательской привязки службы по–прежнему выполняется защита с помощью проверки подлинности NTLM.  
  
 Выполните следующие действия для создания пользовательской службы привязки для службы WCF.  
  
#### <a name="to-create-a-custom-service-binding-for-the-wcf-service-hosted-inside-the-aspnet-development-server"></a>Чтобы создать пользовательскую привязку службы для службы WCF, работающей под ASP.NET Development Server  
  
1. Откройте файл Web.config для службы WCF, которая вызывает исключение.  
  
2. Введите следующую информацию в файл Web.config.  
  
   ```  
   <bindings>  
     <customBinding>  
       <binding name="Service1Binding">  
         <transactionFlow />  
         <textMessageEncoding />  
         <httpTransport authenticationScheme="Ntlm" />  
       </binding>  
     </customBinding>  
   </bindings>  
   ```  
  
3. Сохраните изменения и закройте файл Web.config.  
  
4. В коде WCF или веб–службы измените значение конечной точки на следующее:  
  
   ```  
   <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />  
   ```  
  
    Это гарантирует, что служба использует пользовательскую привязку.  
  
5. Добавьте ссылку на эту службу в веб–приложение, которое обращается к службе. (В диалоговом окне **Добавить ссылку на службу** добавьте ссылку на службу, так же как для исходной службы, которая создавала исключения.)  
  
   Выполните следующие действия для отключения безопасности NTLM при работе со ссылкой на службу WCF.  
  
> [!IMPORTANT]
>  Не рекомендуется отключать безопасность NTLM. Это может представлять угрозу безопасности.  
  
#### <a name="to-turn-off-ntlm-security"></a>Чтобы отключить безопасность NTLM  
  
1.  В **Обозревателе решений**щелкните правой кнопкой мыши имя веб–узла, затем **Страницы свойств**.  
  
2.  Выберите пункт **Параметры запуска**, а затем снимите флажок **Проверка подлинности NTLM** .  
  
3.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 <xref:System.ServiceModel.Security.MessageSecurityException>   
 [Использование помощника по исключениям](http://msdn.microsoft.com/library/e0a78c50-7318-4d54-af51-40c00aea8711)