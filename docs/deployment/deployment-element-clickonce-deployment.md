---
title: '&lt;развертывание&gt; элемент (развертывание ClickOnce) | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e919574ffaa6b1e5545f4c97685722a3017c2182
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823155"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;развертывание&gt; элемент (развертывание ClickOnce)
Идентифицирует атрибуты, используемые для развертывания обновлений и доступа к системе.  

## <a name="syntax"></a>Синтаксис  

```xml  

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
 Элемент `deployment` является обязательным и находится в пространстве имен `urn:schemas-microsoft-com:asm.v1` . Элемент имеет следующие атрибуты.  


| Атрибут | Описание |
|--------------------------| - |
| `install` | Обязательно. Указывает, определяет ли это приложение свое присутствие на Windows **запустить** меню и панели управления **Установка и удаление программ** приложения. Допустимые значения: `true` и `false`. Если `false`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] всегда будет выполняться последнюю версию этого приложения из сети, а не распознает `subscription` элемент. |
| `minimumRequiredVersion` | Необязательный. Указывает минимальную версию этого приложения, можно запустить на клиентском компьютере. Если номер версии приложения меньше, чем номер версии в манифесте развертывания, приложение не запустится. Номера версий должен быть указан в формате `N.N.N.N`, где `N` является целое число без знака. Если `install` атрибут `false`, `minimumRequiredVersion` не должен быть установлен. |
| `mapFileExtensions` | Необязательный. По умолчанию — `false`. Если `true`, все файлы в развертывании должны иметь расширение .deploy. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] удалит это расширение этих файлов сразу после загрузки файлов с веб-сервера. При публикации приложения с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], он автоматически добавляет это расширение ко всем файлам. Этот параметр разрешает все файлы в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания для загрузки с веб-сервера, который блокирует передачу файлов, заканчивающиеся на «небезопасный» расширения, например .exe. |
| `disallowUrlActivation` | Необязательный. По умолчанию — `false`. Если `true`, предотвращает установленного приложения при запуске, щелкнув URL-адрес или введя URL-адреса в Internet Explorer. Если `install` атрибут не задан, этот атрибут игнорируется. |
| `trustURLParameters` | Необязательный. По умолчанию — `false`. Если `true`, позволяет URL-адрес должен содержать параметры строки запроса, которые передаются в приложение, много like аргументы командной строки передаются в приложение командной строки. Дополнительные сведения см. в разделе [как: получить данные строки запроса в интерактивном приложении ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Если `disallowUrlActivation` атрибут `true`, `trustUrlParameters` должен быть исключен из манифеста, либо явно задано значение `false`. |

 `deployment` Элемент также содержит следующие дочерние элементы.  

## <a name="subscription"></a>subscription  
 Необязательный. Содержит `update` элемент. У элемента `subscription` нет атрибутов. Если `subscription` элемент не существует, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения никогда не будет проверять наличие обновлений. Если `install` атрибут `deployment` элемент является `false`, `subscription` элемент обрабатывается, так как [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение, запускаемое из сети, всегда использует последнюю версию.  

## <a name="update"></a>обновить  
 Обязательно. Этот элемент является дочерним элементом `subscription` элемент и содержит либо `beforeApplicationStartup` или `expiration` элемент. `beforeApplicationStartup` и `expiration` невозможно указать одновременно в одном манифесте развертывания.  

 У элемента `update` нет атрибутов.  

## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 Необязательный. Этот элемент является дочерним элементом `update` элемента и не имеет атрибутов. Когда `beforeApplicationStartup` существует элемент, приложение будет заблокирован при [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] проверяет наличие обновлений, если клиент находится в сети. Если этот элемент не существует, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] будет проверять наличие обновлений, основываясь на значениях, заданных для `expiration` элемент. `beforeApplicationStartup` и `expiration` невозможно указать одновременно в одном манифесте развертывания.  

## <a name="expiration"></a>истечение срока действия  
 Необязательный. Этот элемент является дочерним элементом `update` элемент, и не имеет дочерних элементов. `beforeApplicationStartup` и `expiration` невозможно указать одновременно в одном манифесте развертывания. Когда происходит проверка обновлений и обнаружении обновленной версии, новая версия кэшируется во время выполнения существующей версии. Затем устанавливает новую версию при следующем запуске [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения.  

 `expiration` Элемент поддерживает следующие атрибуты.  

|Атрибут|Описание|  
|---------------|-----------------|  
|`maximumAge`|Обязательно. Определяет, как старый текущее обновление станет прежде чем приложение выполняет проверку обновлений. Единица времени определяется `unit` атрибута.|  
|`unit`|Обязательно. Указывает единицу времени для `maximumAge`. Допустимые единицы измерения: `hours`, `days`, и `weeks`.|  

## <a name="deploymentprovider"></a>deploymentProvider  
 Для .NET Framework 2.0, этот элемент является обязательным, если манифест развертывания содержит `subscription` раздел. Для платформы .NET Framework 3.5 и более поздних версиях этот элемент является необязательным и по умолчанию для сервера и путь к файлу, в котором была обнаружена манифеста развертывания.  

 Этот элемент является дочерним по отношению к элементу `deployment` и содержит следующий атрибут.  


| Атрибут | Описание |
|------------| - |
| `codebase` | Обязательно. Указывает расположение, как универсальный код ресурса (URI), манифест развертывания, который используется для обновления [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. Этот элемент также позволяет переадресовывать расположение обновлений для установок на основе компакт-диска. Должен быть допустимым URI. |

## <a name="remarks"></a>Примечания  
 Можно настроить ваш [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение для проверки на наличие обновлений при запуске, проверять наличие обновлений после запуска или никогда не проверять наличие обновлений. Чтобы проверить наличие обновлений при запуске, убедитесь, что `beforeApplicationStartup` элемент существует в группе `update` элемент. Сканирование на наличие обновлений после запуска, убедитесь, что `expiration` элемент существует в группе `update` элемент, и что предоставлены интервалов обновления.  

 Чтобы отключить, проверка наличия обновлений, удалите `subscription` элемент. При указании в манифесте развертывания, никогда не проверять наличие обновлений, можно по-прежнему вручную проверить наличие обновлений с помощью <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> метод.  

 Дополнительные сведения о связи deploymentProvider для обновлений, см. в разделе [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  

## <a name="examples"></a>Примеры  
 В следующем примере кода показано `deployment` элемент [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест развертывания. В примере используется `deploymentProvider` элемент, чтобы указать расположение предпочтительный обновлений.  

```xml  
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