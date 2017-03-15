---
title: "Элемент &lt;entryPoint&gt; (приложение ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#commandLine"
  - "urn:schemas-microsoft-com:asm.v2#entryPoint"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<entryPoint> - элемент [манифест приложения ClickOnce]"
  - "манифесты [ClickOnce], entryPoint - элемент"
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
caps.latest.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 33
---
# Элемент &lt;entryPoint&gt; (приложение ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Идентифицирует сборку, которая должна выполняться, когда это приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] запускается на клиентском компьютере.  
  
## Синтаксис  
  
```  
  
      <entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  
  
## Элементы и атрибуты  
 Элемент `entryPoint` является обязательным и находится в пространстве имен `urn:schemas-microsoft-com:asm.v2`.  В манифесте приложения может быть определен только один элемент `entryPoint`.  
  
 Элемент `entryPoint` имеет следующий атрибут.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`name`|Необязательный.  Это значение не используется платформой .NET Framework.|  
  
 `entryPoint` имеет следующие элементы.  
  
## assemblyIdentity  
 Обязательный.  Роль `assemblyIdentity` и его атрибутов определена в [Элемент \<assemblyIdentity\>](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 Атрибут `processorArchitecture` этого элемента и атрибут `processorArchitecture`, определенный в `assemblyIdentity` в другом месте манифеста приложения должны совпадать.  
  
## commandLine  
 Обязательный.  Должен быть дочерним элементом элемента `entryPoint`.  Он не имеет дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`file`|Обязательный.  Локальная ссылка на начальную сборку для приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Это значение не может содержать разделители в виде косой черты \(\/\) или обратной косой черты \(\\\).|  
|`parameters`|Обязательный.  Описывает действие, которое необходимо выполнить с точкой входа.  Только допустимое значение `run`; если задается пустая строка, то `run` предполагается.|  
  
## customHostRequired  
 Необязательный.  Если включен, то указывает, что это развертывание содержит компонент, который будет развернут в настраиваемом узле и не является автономным приложением.  
  
 Если этот элемент присутствует, то элементы `assemblyIdentity` и `commandLine` присутствовать не должны.  Если они есть, то [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] сообщит об ошибке проверки во время установки.  
  
 Этот элемент не имеет атрибутов дочерних элементов.  
  
## customUX  
 Необязательный.  Указывает, что приложение установлено и поддерживается пользовательским установщиком и для него не создана запись в меню "Пуск", ярлык или запись в разделе "Установка и удаление программ".  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Приложение, которое содержит элемент customUX, должно предоставлять пользовательский установщик, использующий класс <xref:System.Deployment.Application.InPlaceHostingManager> для выполнения операций установки.  Приложение с этим элементом нельзя установить, дважды щелкнув его манифест или загрузчик необходимых компонентов setup.exe.  Пользовательский установщик может создавать элементы меню" Пуск", ярлыки и записи раздела "Установка и удаление программ".  Если пользовательский установщик не создает запись "Установка и удаление программ", то он должен сохранить идентификатор подписки, предоставляемый свойством <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> и предоставить пользователю возможность последующего удаления приложения путем вызова метода <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A>.  Дополнительные сведения см. в разделе [Пошаговое руководство. Создание пользовательского установщика для приложения ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## Заметки  
 Этот элемент идентифицирует сборку и точку входа для приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Нельзя использовать `commandLine` для ввода параметров в приложение во время его выполнения.  Можно обратиться к параметрам строки запроса для развертывания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] из приложения <xref:System.AppDomain>.  Дополнительные сведения см. в разделе [Практическое руководство. Извлечение сведений строки запроса в интернет\-приложении ClickOnce](../Topic/How%20to:%20Retrieve%20Query%20String%20Information%20in%20an%20Online%20ClickOnce%20Application.md).  
  
## Пример  
 В следующем примере кода показан элемент `entryPoint` файла  манифеста приложения для приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Данный пример кода является частью большего примера, приведенного для раздела [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md).  
  
```  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  
  
## См. также  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)