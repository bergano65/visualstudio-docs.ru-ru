---
title: '&lt;&gt;элемент entryPoint (приложение ClickOnce) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 9ce9fcbddf54dff0ee8574d0c2a5a3df4d8b5c7e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193497"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;&gt;элемент entryPoint (приложение ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет сборку, которая должна быть выполнена при [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] запуске приложения на клиентском компьютере.  
  
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
 Элемент `entryPoint` является обязательным и находится в пространстве имен `urn:schemas-microsoft-com:asm.v2` . `entryPoint`В манифесте приложения может быть определен только один элемент.  
  
 Элемент `entryPoint` имеет указанный ниже атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`name`|Необязательный элемент. Это значение не используется .NET Framework.|  
  
 У элемента`entryPoint` имеются перечисленные ниже элементы.  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Обязательный. Роль `assemblyIdentity` и ее атрибуты определены в [ \<assemblyIdentity> элементе](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 `processorArchitecture`Атрибут этого элемента и `processorArchitecture` атрибут, определенный в другой части `assemblyIdentity` манифеста приложения, должны совпадать.  
  
## <a name="commandline"></a>commandLine  
 Обязательный. Должен быть дочерним по отношению к `entryPoint` элементу. Он не имеет дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`file`|Обязательный. Локальная ссылка на стартовую сборку для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения. Это значение не может содержать разделители пути косой черты (/) или обратной косой черты ( \\ ).|  
|`parameters`|Обязательный. Описывает действие, которое необходимо выполнить с точкой входа. Единственное допустимое значение — `run` ; Если указана пустая строка, `run` то предполагается.|  
  
## <a name="customhostrequired"></a>кустомхострекуиред  
 Необязательный элемент. Если включено, указывает, что это развертывание содержит компонент, который будет развернут внутри пользовательского узла и не является автономным приложением.  
  
 Если этот элемент имеется, `assemblyIdentity` `commandLine` элементы и также не должны присутствовать. Если это так, при [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] установке будет вызвана ошибка проверки.  
  
 У этого элемента нет атрибутов и дочерних элементов.  
  
## <a name="customux"></a>customUX  
 Необязательный элемент. Указывает, что приложение установлено и обслуживается пользовательским установщиком и не создает запись меню "Пуск", ярлык или "Установка и удаление программ".  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Приложение, содержащее элемент customUX, должно предоставлять пользовательский установщик, который использует <xref:System.Deployment.Application.InPlaceHostingManager> класс для выполнения операций установки. Приложение с этим элементом нельзя установить, дважды щелкнув его манифест или setup.exe загрузчик необходимых компонентов. Пользовательский установщик может создавать записи меню "Пуск", ярлыки, а также записи "Установка и удаление программ". Если пользовательский установщик не создает запись "Установка и удаление программ", он должен хранить идентификатор подписки, предоставленный <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> свойством, и позволить пользователю удалить приложение позже, вызвав <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> метод. Дополнительные сведения см. [в разделе Пошаговое руководство. Создание пользовательского установщика для приложения ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## <a name="remarks"></a>Remarks  
 Этот элемент определяет сборку и точку входа для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения.  
  
 Нельзя использовать `commandLine` для передачи параметров в приложение во время выполнения. Можно получить доступ к параметрам строки запроса для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания из приложения <xref:System.AppDomain> . Дополнительные сведения см. [в разделе инструкции. Получение сведений о строке запроса в приложении ClickOnce в сети](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан `entryPoint` элемент в манифесте приложения для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения. Этот пример кода является частью большого примера, приведенного в разделе [манифеста приложения ClickOnce](../deployment/clickonce-application-manifest.md) .  
  
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
  
## <a name="see-also"></a>См. также:  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
