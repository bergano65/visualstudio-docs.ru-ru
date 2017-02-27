---
title: "Элемент &lt;deployment&gt; (развертывание ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#subscription"
  - "urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup"
  - "urn:schemas-microsoft-com:asm.v2#deploymentProvider"
  - "urn:schemas-microsoft-com:asm.v2#update"
  - "urn:schemas-microsoft-com:asm.v2#deployment"
  - "urn:schemas-microsoft-com:asm.v2#expiration"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<deployment> - элемент [манифест развертывания ClickOnce]"
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 30
---
# Элемент &lt;deployment&gt; (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определение атрибутов, используемых для развертывания обновлений и доступа к системе.  
  
## Синтаксис  
  
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
  
## Элементы и атрибуты  
 Элемент `deployment` является обязательным и находится в пространстве имен `urn:schemas-microsoft-com:asm.v1`.  Элемент имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`install`|Обязательный.  Указывает, будет ли приложение находиться в меню "**Пуск**" и в диалоговом окне "**Установка и удаление программ**" панели управления.  Допустимые значения: `true` и `false`.  Если атрибут имеет значение `false`, приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] будет всегда запускать последнюю версию приложения из сети и не будет распознавать элемент `subscription`.|  
|`minimumRequiredVersion`|Необязательный.  Задает минимальный номер версии приложения, запускаемого на клиентском компьютере.   Если номер версии приложения меньше, чем номер версии, поддерживаемой в манифесте развертывания, приложение не запустится.  Номера версий должны быть указаны в формате `N.N.N.N`, где `N` – целое число без знака.  Если атрибут `install` имеет значение `false`, нельзя задать значение атрибута `minimumRequiredVersion`.|  
|`mapFileExtensions`|Необязательный.  По умолчанию используется значение `false`.  Если `true`, то все файлы в развертывании должны иметь расширение DEPLOY.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] удалит это расширение сразу после загрузки этих файлов с веб\-сервера.  Если приложение опубликовано с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], то данное расширение автоматически добавляется ко всем файлам.  Этот параметр позволяет загружать все файлы, развертываемые с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], с веб\-сервера, который блокирует передачу файлов, имеющих небезопасное расширение \(например, передачу EXE\-файлов\).|  
|`disallowUrlActivation`|Необязательный.  По умолчанию используется значение `false`.  Установка значения `true` позволяет предотвратить установку приложения по щелчку URL\-адреса или путем ввода URL\-адреса в веб\-обозреватель Internet Explorer.  Если атрибут `install` отсутствует, то этот атрибут игнорируется.|  
|`trustURLParameters`|Необязательный.  По умолчанию используется значение `false`.  Установка значения `true` разрешает URL\-адресам содержать параметры строки запроса, передаваемые приложению таким же образом, как аргументы командной строки передаются приложению командной строки.  Дополнительные сведения см. в разделе [Практическое руководство. Извлечение сведений строки запроса в интернет\-приложении ClickOnce](../Topic/How%20to:%20Retrieve%20Query%20String%20Information%20in%20an%20Online%20ClickOnce%20Application.md).<br /><br /> Если атрибут `disallowUrlActivation` имеет значение `true`, то атрибут `trustUrlParameters` должен быть либо исключен из манифеста, либо явно установлен в `false`.|  
  
 Элемент `deployment` может содержать следующие дочерние элементы.  
  
## подписка  
 Необязательный.  Содержит элемент `update`.  У элемента `subscription` отсутствуют атрибуты.  Если элемент `subscription` не существует, то приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] никогда не будет искать обновления.  Если атрибут `install` элемента `deployment` имеет значение `false`, элемент `subscription` игнорируется, т.к. приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], запускаемое из сети, всегда использует последнюю версию.  
  
## update  
 Обязательный.  Этот элемент является дочерним для элемента `subscription` и содержит элемент `beforeApplicationStartup` или `expiration`.  Элементы `beforeApplicationStartup` и `expiration` не могут оба быть заданы в одном манифесте развертывания.  
  
 У элемента `update` отсутствуют атрибуты.  
  
## beforeApplicationStartup  
 Необязательный.  Этот элемент является дочерним по отношению к элементу `update` и не имеет атрибутов.  Если элемент `beforeApplicationStartup` существует, то при подключении клиентского компьютера к сети приложение будет блокировать проверки [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] на наличие обновлений.  Если этот элемент не существует, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] сначала будет проверять обновления на основе значений, указанных для элемента `expiration`.  Элементы `beforeApplicationStartup` и `expiration` не могут оба быть заданы в одном манифесте развертывания.  
  
## expiration  
 Необязательный.  Этот элемент является дочерним для элемента `update` и не имеет дочерних элементов.  Элементы `beforeApplicationStartup` и `expiration` не могут оба быть заданы в одном манифесте развертывания.  Когда происходит проверка обновлений и обнаруживается обновленная версия, новая версия кэшируется во время выполнения существующей версии.  При следующем запуске приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] устанавливается новая версия.  
  
 Элемент `expiration` поддерживает следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`maximumAge`|Обязательный.  Указывает давность текущего обновления до того, как приложение выполнит проверку на наличие обновлений.  Единица измерения времени задается атрибутом `unit`.|  
|`unit`|Обязательный.  Указывает единицу времени для атрибута `maximumAge`.  Допустимыми значениями являются `hours`, `days` и `weeks`.|  
  
## deploymentProvider  
 В .NET Framework 2.0 этот элемент является обязательным, если манифест развертывания содержит раздел `subscription`.  Для платформы .NET Framework 3.5 этот элемент не является обязательным и указывает путь к серверу и файлу, в котором производится поиск манифеста развертывания.  
  
 Этот элемент является дочерним элементом для элемента `deployment` и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`codebase`|Обязательный.  Указывает расположение манифеста развертывания в формате универсального кода ресурса \(URI\), используемого приложением [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] для выполнения обновления.  Этот элемент также позволяет переадресовывать расположение обновлений для установок с компакт\-дисков.  Должен являться допустимым URI.|  
  
## Заметки  
 Настройку приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] можно выполнить таким образом, чтобы поиск обновлений осуществлялся при запуске, после запуска или не производился вообще.  При выборе поиска обновлений при запуске убедитесь, что элемент `beforeApplicationStartup` находится под элементом `update`.  При выборе поиска обновлений после запуска убедитесь, что элемент `expiration` находится под элементом `update`, а требуемые интервалы обновления заданы.  
  
 Для отмены проверки на наличие обновлений необходимо удалить элемент `subscription`.  При установки в манифесте развертывания отмены проверки наличия обновлений данную проверку можно выполнить вручную с помощью метода <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A>.  
  
 Дополнительные сведения о том, как элемент deploymentProvider связан с обновлениями, см. в разделе [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## Примеры  
 В следующем примере кода показан элемент `deployment` в манифесте развертывания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  В примере используется элемент `deploymentProvider` для указания предпочитаемого расположения обновления.  
  
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
  
## См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)