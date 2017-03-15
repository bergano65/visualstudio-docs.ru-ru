---
title: "Элемент &lt;dependency&gt; (приложение ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#osVersionInfo"
  - "urn:schemas-microsoft-com:asm.v2#os"
  - "http://www.w3.org/2000/09/xmldsig#Transform"
  - "urn:schemas-microsoft-com:asm.v2#dependency"
  - "http://www.w3.org/2000/09/xmldsig#DigestValue"
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
  - "http://www.w3.org/2000/09/xmldsig#DigestMethod"
  - "http://www.w3.org/2000/09/xmldsig#Transforms"
  - "urn:schemas-microsoft-com:asm.v2#hash"
  - "urn:schemas-microsoft-com:asm.v2#dependentAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<dependency> - элемент [манифест приложения ClickOnce]"
  - "манифесты [ClickOnce], dependency - элемент"
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
caps.latest.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 34
---
# Элемент &lt;dependency&gt; (приложение ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Идентифицирует платформу или зависимость сборки, которая требуется для приложения.  
  
## Синтаксис  
  
```  
  
      <dependency>  
   <dependentOS  
      supportURL  
      description  
   >  
      <osVersionInfo>  
         <os  
            majorVersion  
            minorVersion  
            buildNumber  
            servicePackMajor  
            servicePackMinor  
            productType  
            suiteType  
         />   
      </osVersionInfo>  
   </dependentOS>  
   <dependentAssembly  
      dependencyType  
      allowDelayedBinding  
      group  
      codeBase  
      size  
   >  
      <assemblyIdentity  
         name  
         version  
         processorArchitecture  
         language  
      >  
         <hash>  
            <dsig:Transforms>  
               <dsig:Transform  
                  Algorithm  
            />  
            </dsig:Transforms>  
            <dsig:DigestMethod />  
            <dsig:DigestValue>  
            </dsig:DigestValue>  
    </hash>  
  
      </assemblyIdentity>  
   </dependentAssembly>  
</dependency>  
```  
  
## Элементы и атрибуты  
 Элемент `dependency` является обязательным.  В одном манифесте приложения может быть несколько экземпляров `dependency`.  
  
 Элемент `dependency` не имеет атрибутов и содержит следующие дочерние элементы.  
  
### dependentOS  
 Необязательный.  Содержит элемент `osVersionInfo`.  Элементы `dependentOS` и `dependentAssembly` являются взаимоисключающими: один или другой должен существовать для элемента `dependency`, но не оба.  
  
 `dependentOS` поддерживает следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`supportUrl`|Необязательный.  Задает поддержку URL для зависимой платформы.  Этот URL показывается пользователю, если найдена требуемая платформа.|  
|`description`|Необязательный.  В удобочитаемой форме описывает операционную систему, описанную элементом `dependentOS`.|  
  
### osVersionInfo  
 Обязательный.  Этот элемент является дочерним для элемента `dependentOS` и содержит элемент `os`.  Этот элемент не имеет атрибутов.  
  
### os  
 Обязательный.  Этот элемент является дочерним для элемента `osVersionInfo`.  Этот элемент имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`majorVersion`|Обязательный.  Задает старший разряд номера версии операционной системы.|  
|`minorVersion`|Обязательный.  Задает младший разряд номера версии операционной системы.|  
|`buildNumber`|Обязательный.  Задает номер построения операционной системы.|  
|`servicePackMajor`|Обязательный.  Задает старший разряд номера пакета обновления операционной системы.|  
|`servicePackMinor`|Необязательный.  Задает младший разряд номера пакета обновления операционной системы.|  
|`productType`|Необязательный.  Идентифицирует значение типа продукта.  Допустимые значения: `server`, `workstation` и `domainController`.  Например, для Windows 2000 Professional значение этого атрибута — `workstation`.|  
|`suiteType`|Необязательный.  Идентифицирует пакет продуктов, доступный в системе, или тип конфигурации системы.  Допустимые значения: `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted`, и `terminal`.  Например, для Windows 2000 Professional значение этого атрибута — `professional`.|  
  
### dependentAssembly  
 Необязательный.  Содержит элемент `assemblyIdentity`.  Элементы `dependentOS` и `dependentAssembly` являются взаимоисключающими: один или другой должен существовать для элемента `dependency`, но не оба.  
  
 `dependentAssembly` имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`dependencyType`|Обязательный.  Задает тип зависимости.  Допустимые значения: `preprequisite` и `install`.  Сборка `install` устанавливается как часть приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Сборка `prerequisite` должна находиться в глобальном кэше сборок перед установкой приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].|  
|`allowDelayedBinding`|Обязательный.  Указывает на возможность программного запуска сборки во время выполнения.|  
|`group`|Необязательный.  Если атрибут `dependencyType` имеет значение `install`, то данный атрибут указывает именованную группу сборок, которые устанавливаются по требованию.  Дополнительные сведения см. в разделе [Пошаговое руководство. Загрузка сборок по требованию с помощью API развертывания ClickOnce с использованием конструктора](../Topic/Walkthrough:%20Downloading%20Assemblies%20on%20Demand%20with%20the%20ClickOnce%20Deployment%20API%20Using%20the%20Designer.md).<br /><br /> Если значение равно `framework`, а атрибут `dependencyType` имеет значение `prerequisite`, то данный атрибут указывает сборку как часть платформы .NET Framework.  Глобальный кэш сборок для этой сборки не проверяется при установке в [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)] и более поздних версиях.|  
|`codeBase`|Требуется, если атрибут `dependencyType` имеет значение `install`.  Путь к зависимой сборке.  К основанию кода манифеста может быть или абсолютный путь, или относительный путь.  Этим путем должен быть допустимый URI, для того чтобы манифест сборки был допустимым.|  
|`size`|Требуется, если атрибут `dependencyType` имеет значение `install`.  Размер зависимой сборки в байтах.|  
  
### assemblyIdentity  
 Обязательный.  Этот элемент является дочерним элементом `dependentAssembly` и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`name`|Обязательный.  Идентифицирует имя приложения.|  
|`version`|Обязательный.  Задает номер версии приложения в следующем формате: `основной.дополнительный.построение.редакция`.|  
|`publicKeyToken`|Необязательный.  Задает 16\-символьную шестнадцатеричную строку, которая представляет последние 8 байтов хэша `SHA-1` открытого ключа, которым подписывается приложение или сборка.  Открытый ключ доступа, используемый для подписи каталога, должен содержать не менее 2048.|  
|`processorArchitecture`|Необязательный.  Задает процессор.  Действующие значения `x86` для 32\-битового Windows и `I64` для 64\-битового Windows.|  
|`language`|Необязательный.  Идентифицирует две части кодов языка сборки, например EN\-US.|  
  
### hash  
 Элемент `hash` является необязательным дочерним элементом элемента `assemblyIdentity`.  У элемента `hash` отсутствуют атрибуты.  
  
 Для того чтобы гарантировать, что ни один из файлов не был изменен после развертывания, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] использует алгоритмический хэш всех файлов в приложении в качестве проверки защиты.  Если элемент `hash` не включен, такая проверка выполняться не будет. Поэтому не рекомендуется пропускать элемент `hash`.  
  
### dsig:Transforms  
 Элемент `dsig:Transforms` является обязательным дочерним элементом элемента `hash`.  У элемента `dsig:Transforms` отсутствуют атрибуты.  
  
### dsig:Transform  
 Элемент `dsig:Transform` является обязательным дочерним элементом элемента `dsig:Transforms`.  Элемент `dsig:Transform` имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Algorithm`|Алгоритм, используемый для вычисления дайджеста для этого файла.  В настоящее время значением, используемым [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], может быть только `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
### dsig:DigestMethod  
 Элемент `dsig:DigestMethod` является обязательным дочерним элементом элемента `hash`.  Элемент `dsig:DigestMethod` имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Algorithm`|Алгоритм, используемый для вычисления дайджеста для этого файла.  В настоящее время [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] может использовать только значение `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
### dsig:DigestValue  
 Элемент `dsig:DigestValue` является обязательным дочерним элементом элемента `hash`.  У элемента `dsig:DigestValue` отсутствуют атрибуты.  Его текстовое значение – это вычисленный хэш для указанного файла.  
  
## Заметки  
 Все сборки, используемые вашим приложением должны иметь соответствующий элемент `dependency`.  Зависимые сборки не включают сборки, которые должны быть предварительно установлены в кэш глобальной сборки в качестве платформы сборок.  
  
## Пример  
 В следующем примере кода показаны элементы `dependency` в манифесте приложения[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Данный пример кода является частью большего примера, приведенного в разделе [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md).  
  
```  
<dependency>  
  <dependentOS>  
    <osVersionInfo>  
      <os   
        majorVersion="4"   
        minorVersion="10"   
        buildNumber="0"   
        servicePackMajor="0" />  
    </osVersionInfo>  
  </dependentOS>  
</dependency>  
<dependency>  
  <dependentAssembly  
    dependencyType="preRequisite"  
    allowDelayedBinding="true">  
    <assemblyIdentity  
      name="Microsoft.Windows.CommonLanguageRuntime"  
      version="4.0.20506.0" />  
  </dependentAssembly>  
</dependency>  
  
<dependency>  
  <dependentAssembly  
    dependencyType="install"  
    allowDelayedBinding="true"  
    codebase="MyApplication.exe"  
    size="4096">  
    <assemblyIdentity  
      name="MyApplication"  
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## См. также  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Элемент \<dependency\>](../deployment/dependency-element-clickonce-deployment.md)