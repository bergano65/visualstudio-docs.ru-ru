---
title: '&lt;entryPoint&gt; элемент (приложение ClickOnce) | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: beb140a64a415ab1a42f8157e2fafb1d20f9569a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31565254"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;entryPoint&gt; элемент (приложение ClickOnce)
Идентифицирует сборку, которая должна быть выполнена, когда это [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение запускается на клиентском компьютере.  
  
## <a name="syntax"></a>Синтаксис  
  
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
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Элемент `entryPoint` обязателен и находится в пространстве имен `urn:schemas-microsoft-com:asm.v2`. Может существовать только один `entryPoint` , определенному в манифесте приложения.  
  
 `entryPoint` Элемент имеет указанный ниже атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`name`|Необязательный. Это значение не используется платформой .NET Framework.|  
  
 `entryPoint` содержит следующие элементы.  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Обязательно. Роль `assemblyIdentity` и его атрибутов, определенных в [ \<assemblyIdentity > элемент](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 `processorArchitecture` Атрибут этого элемента и `processorArchitecture` атрибуту, определенному в `assemblyIdentity` в другом месте в приложении манифеста должны совпадать.  
  
## <a name="commandline"></a>Командная строка  
 Обязательно. Должен быть дочерним элементом `entryPoint` элемента. Он не имеет дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`file`|Обязательно. Локальную ссылку на сборку для запуска [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. Это значение не может содержать косую черту (/) или обратную косую черту (\\) в качестве разделителей пути.|  
|`parameters`|Обязательно. Описывает действие, выполняемое с точкой входа. Единственным допустимым значением является `run`; Если задано пустой строкой, `run` предполагается.|  
  
## <a name="customhostrequired"></a>customHostRequired  
 Необязательный. Если включен, указывает, что это развертывание содержит компонент, который будет развернут в настраиваемом узле и не является автономным приложением.  
  
 Если этот элемент присутствует, `assemblyIdentity` и `commandLine` элементы не также должны присутствовать. Если они являются [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] будет вызывать ошибку проверки во время установки.  
  
 Этот элемент не имеет атрибутов и дочерних элементов.  
  
## <a name="customux"></a>customUX  
 Необязательный. Указывает, что приложение устанавливается и обслуживается пользовательский установщик и не создать запись меню Пуск, контекстное или добавить или удалить запись программы.  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Приложения, которое содержит элемент customUX необходимо предоставить пользовательский установщик, использующий <xref:System.Deployment.Application.InPlaceHostingManager> классом для выполнения установки операций. Не удается установить приложение с помощью этого элемента, дважды щелкнув его манифест или setup.exe загрузчик необходимых компонентов. Пункты меню Пуск, ярлыков и записей, Установка и удаление программ, можно создать пользовательский установщик. Если пользовательский установщик не создает запись Установка и удаление программ, его необходимо сохранить идентификатор подписки, предоставляемые <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> свойство и включение пользователя удалить приложение позднее путем вызова <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> метод. Дополнительные сведения см. в разделе [Пошаговое руководство: Создание пользовательского установщика для приложения ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## <a name="remarks"></a>Примечания  
 Этот элемент идентифицирует сборку и точку входа для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения.  
  
 Нельзя использовать `commandLine` для передачи параметров в приложение во время выполнения. Можно открыть параметры строки запроса для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания в приложении <xref:System.AppDomain>. Дополнительные сведения см. в разделе [как: получение сведений строки запроса в приложение ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан `entryPoint` элемента в манифесте приложения для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. Данный пример кода является частью большего примера, приведенного для [манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md) раздела.  
  
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
  
## <a name="see-also"></a>См. также  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)