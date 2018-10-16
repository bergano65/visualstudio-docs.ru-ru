---
title: '&lt;entryPoint&gt; элемент (приложение ClickOnce) | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: da308de644dfc73d9364b65e21e820d6fc6c2a8a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255323"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;entryPoint&gt; элемент (приложение ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Идентифицирует сборку, которая должна быть выполнена, когда это [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложение запускается на клиентском компьютере.  
  
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
 Элемент `entryPoint` является обязательным и находится в пространстве имен `urn:schemas-microsoft-com:asm.v2` . Может существовать только один `entryPoint` элементу, определенному в манифесте приложения.  
  
 Элемент `entryPoint` имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`name`|Необязательный. Это значение не используется платформой .NET Framework.|  
  
 У элемента`entryPoint` имеются перечисленные ниже элементы.  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Обязательно. Роль `assemblyIdentity` и его атрибуты, определенные в [ \<assemblyIdentity > элемент](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 `processorArchitecture` Атрибут этого элемента и `processorArchitecture` атрибутом, определенным в `assemblyIdentity` в другом месте в приложении манифест должен соответствовать.  
  
## <a name="commandline"></a>commandLine  
 Обязательно. Должен быть дочерним элементом `entryPoint` элемент. Он не имеет дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`file`|Обязательно. Локальную ссылку на сборку для запуска [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения. Это значение не может содержать косую черту (/) или обратную косую черту (\\) разделители путей.|  
|`parameters`|Обязательно. Описывает действие, выполняемое с точкой входа. Единственным допустимым значением является `run`; Если передается пустая строка, `run` предполагается, что.|  
  
## <a name="customhostrequired"></a>customHostRequired  
 Необязательный. Если включен, указывает, что это развертывание содержит компонент, который будет развернут в настраиваемом узле, а не является автономным приложением.  
  
 Если этот элемент присутствует, `assemblyIdentity` и `commandLine` элементы не также должен присутствовать. Если Да, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] вызовут ошибки проверки во время установки.  
  
 Этот элемент не имеет атрибутов и дочерних элементов.  
  
## <a name="customux"></a>customUX  
 Необязательный. Указывает, что приложение устанавливается и обслуживается пользовательский установщик и не создает запись меню Пуск, клавиш или добавить и удалить запись программы.  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Приложения, содержащего элемент customUX необходимо предоставить пользовательский установщик, использующий <xref:System.Deployment.Application.InPlaceHostingManager> классом для выполнения установки операций. Приложения с помощью этого элемента невозможно установить, дважды щелкнув его готовности к установке загрузчика setup.exe или манифеста. Можно создать пользовательский установщик, пункты меню Пуск, ярлыки и записи, Установка и удаление программ. Если пользовательский установщик не выполняет запись Установка и удаление программ, его необходимо сохранить идентификатор подписки, предоставляемый <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> свойство и включите пользователя для удаления приложения позже, вызвав <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> метод. Дополнительные сведения см. в разделе [Пошаговое руководство: Создание пользовательского установщика для приложения ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## <a name="remarks"></a>Примечания  
 Этот элемент определяет, сборки и точки входа для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения.  
  
 Нельзя использовать `commandLine` для передачи параметров в приложение во время выполнения. Можно открыть параметры строки запроса для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания из приложения <xref:System.AppDomain>. Дополнительные сведения см. в разделе [как: получить данные строки запроса в интерактивном приложении ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано `entryPoint` элемента в манифесте приложения для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения. Данный пример кода является частью большего примера для [манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md) раздела.  
  
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
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)



