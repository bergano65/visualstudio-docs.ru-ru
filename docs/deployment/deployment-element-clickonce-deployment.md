---
title: '&lt;развертывание&gt; элемент (развертывание ClickOnce) | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 30
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 0caff13f84208152b3fa2ff4e56a7a2c7f0b6dd7
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2018
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;развертывание&gt; элемент (развертывание ClickOnce)
Идентифицирует атрибуты, используемые для развертывания обновлений и доступа к системе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Элемент `deployment` обязателен и находится в пространстве имен `urn:schemas-microsoft-com:asm.v1`. Элемент имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`install`|Обязательно. Указывает, является ли это приложение определяет свое присутствие на Windows **запустить** меню и панели управления **Установка и удаление программ** приложения. Допустимые значения: `true` и `false`. Если `false`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] всегда будет запустите последнюю версию этого приложения из сети, а не распознает `subscription` элемента.|  
|`minimumRequiredVersion`|Необязательный. Указывает минимальную версию этого приложения, выполняющиеся на клиентском компьютере. Если номер версии приложения меньше, чем номер версии, поддерживаемой в манифесте развертывания, приложение не запустится. Номер версии должен быть указан в формате `N.N.N.N`, где `N` является целым числом без знака. Если `install` атрибут `false`, `minimumRequiredVersion` не должно быть задано.|  
|`mapFileExtensions`|Необязательный. По умолчанию — `false`. Если `true`, все файлы в развертывании должны иметь расширение .deploy. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] удалит это расширение этих файлов сразу после загрузки файлов с веб-сервера. При публикации приложения с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], автоматически добавляет это расширение ко всем файлам. Этот параметр позволяет все файлы в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания для загрузки с веб-сервера, который блокирует передачу файлов, заканчивающиеся на «unsafe» расширения, такие как .exe.|  
|`disallowUrlActivation`|Необязательный. По умолчанию — `false`. Если `true`, предотвращает установленного приложения при запуске, щелкнув URL-адрес или URL-адрес в Internet Explorer. Если `install` атрибут не задан, этот атрибут игнорируется.|  
|`trustURLParameters`|Необязательный. По умолчанию — `false`. Если `true`, позволяет URL-адрес для хранения параметров строки запроса, которые передаются в приложение, объем like аргументы командной строки передаются приложению командной строки. Дополнительные сведения см. в разделе [как: получение сведений строки запроса в приложение ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Если `disallowUrlActivation` атрибут `true`, `trustUrlParameters` должен быть исключен из манифеста, либо явно задано значение `false`.|  
  
 `deployment` Элемент также содержит следующие дочерние элементы.  
  
## <a name="subscription"></a>subscription  
 Необязательный. Содержит `update` элемента. `subscription` Элемент не имеет атрибутов. Если `subscription` элемент не существует, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения никогда не будет искать обновления. Если `install` атрибут `deployment` элемент `false`, `subscription` элемент игнорируется, так как [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение, запускаемое из сети, всегда использует последнюю версию.  
  
## <a name="update"></a>обновить  
 Обязательно. Этот элемент является дочерним элементом `subscription` элемент и может содержать `beforeApplicationStartup` или `expiration` элемент. `beforeApplicationStartup` и `expiration` невозможно указать одновременно в одном манифесте развертывания.  
  
 `update` Элемент не имеет атрибутов.  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 Необязательный. Этот элемент является дочерним элементом `update` элемента и не имеет атрибутов. Когда `beforeApplicationStartup` элемент существует, приложение будет заблокирован при [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] проверяет наличие обновлений, если клиент подключен к сети. Если этот элемент не существует, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] будет проверять наличие обновлений, в зависимости от значения, указанные для `expiration` элемента. `beforeApplicationStartup` и `expiration` невозможно указать одновременно в одном манифесте развертывания.  
  
## <a name="expiration"></a>истечение срока действия  
 Необязательный. Этот элемент является дочерним элементом `update` элемент, и не имеет дочерних элементов. `beforeApplicationStartup` и `expiration` невозможно указать одновременно в одном манифесте развертывания. Когда происходит проверка обновлений и обнаруживается обновленная версия, новая версия кэшируется во время выполнения существующей версии. При следующем запуске устанавливается новая версия [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения.  
  
 `expiration` Элемент поддерживает следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`maximumAge`|Обязательно. Определяет, насколько стара текущего обновления должны стать прежде чем приложение выполнит проверку обновлений. Единица времени определяется `unit` атрибута.|  
|`unit`|Обязательно. Указывает единицу времени для `maximumAge`. Допустимые единицы `hours`, `days`, и `weeks`.|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 Для платформы .NET Framework 2.0, этот элемент является обязательным, если манифест развертывания содержит `subscription` раздела. Для платформы .NET Framework 3.5 и более поздних версиях этот элемент является необязательным и указывает сервер и путь к файлу, в котором производится поиск манифеста развертывания.  
  
 Этот элемент является дочерним по отношению к элементу `deployment` и содержит следующий атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`codebase`|Обязательно. Определяет расположение, как универсальный идентификатор ресурса (URI), манифест развертывания, который используется для обновления [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. Этот элемент также позволяет переадресовывать расположение обновлений для установки с Компакт диска. Должно быть допустимым URI.|  
  
## <a name="remarks"></a>Примечания  
 Можно настроить на [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] проверять наличие обновлений после запуска приложения для проверки наличия обновлений при запуске, или никогда не проверять наличие обновлений. Чтобы проверить наличие обновлений при запуске, убедитесь, что `beforeApplicationStartup` элемент существует в группе `update` элемента. Сканирование на наличие обновлений после запуска приложения, убедитесь, что `expiration` элемент существует в группе `update` элемент, а также предоставление интервалов обновления.  
  
 Чтобы отключить проверку обновлений, удалите `subscription` элемента. При указании в манифесте развертывания, никогда не проверять наличие обновлений вручную по-прежнему можно проверить наличие обновлений с помощью <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> метод.  
  
 Дополнительные сведения о как deploymentProvider относится к обновлениям см. в разделе [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере кода показан `deployment` элемент в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест развертывания. В примере используется `deploymentProvider` , чтобы указать расположение предпочтительный обновлений.  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## <a name="see-also"></a>См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)