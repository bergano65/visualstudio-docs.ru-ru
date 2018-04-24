---
title: '&lt;зависимость&gt; элемент (приложение ClickOnce) | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c5d84dba671d1fddda0569015d936b95e5e58d1d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;зависимость&gt; элемент (приложение ClickOnce)
Идентифицирует платформу или зависимость сборки, необходимые для приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
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
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `dependency` Элемент является обязательным. Может существовать несколько экземпляров `dependency` в одном манифесте приложения.  
  
 `dependency` Элемент не имеет атрибутов и содержит следующие дочерние элементы.  
  
### <a name="dependentos"></a>dependentOS  
 Необязательный. Содержит `osVersionInfo` элемента. `dependentOS` И `dependentAssembly` элементы являются взаимоисключающими: одно из них должен быть `dependency` элемент, но не оба.  
  
 `dependentOS` поддерживает следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`supportUrl`|Необязательный. Указывает URL-адрес поддержки для зависимой платформы. Этот URL-адрес отображается для пользователя, если найдена требуемая платформа.|  
|`description`|Необязательный. Описывает операционной системы, описываемых в удобочитаемой форме `dependentOS` элемента.|  
  
### <a name="osversioninfo"></a>osVersionInfo  
 Обязательно. Этот элемент является дочерним по отношению к элементу `dependentOS` и содержит элемент `os`. Этот элемент не содержит атрибуты.  
  
### <a name="os"></a>ОС  
 Обязательно. Этот элемент является дочерним по отношению к элементу `osVersionInfo`. Этот элемент содержит следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`majorVersion`|Обязательно. Указывает основной номер версии операционной системы.|  
|`minorVersion`|Обязательно. Задает дополнительный номер версии операционной системы.|  
|`buildNumber`|Обязательно. Указывает номер сборки операционной системы.|  
|`servicePackMajor`|Обязательно. Указывает основной номер пакета обновления операционной системы.|  
|`servicePackMinor`|Необязательный. Указывает дополнительный номер пакета обновления операционной системы.|  
|`productType`|Необязательный. Определяет значение типа продукта. Допустимые значения: `server`, `workstation` и `domainController`. Например, для Windows 2000 Professional — это значение атрибута `workstation`.|  
|`suiteType`|Необязательный. Определяет набор продуктов, доступных в системе, или тип конфигурации системы. Допустимые значения: `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted`, и `terminal`. Например, для Windows 2000 Professional — это значение атрибута `professional`.|  
  
### <a name="dependentassembly"></a>dependentAssembly  
 Необязательный. Содержит `assemblyIdentity` элемента. `dependentOS` И `dependentAssembly` элементы являются взаимоисключающими: одно из них должен быть `dependency` элемент, но не оба.  
  
 `dependentAssembly` имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`dependencyType`|Обязательно. Указывает тип зависимости. Допустимые значения: `preprequisite` и `install`. `install` Сборка устанавливается как часть [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. Объект `prerequisite` сборки должны присутствовать в глобальный кэш сборок (GAC) перед [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] можно установить приложения.|  
|`allowDelayedBinding`|Обязательно. Указывает, является ли сборка может быть загружена программными средствами во время выполнения.|  
|`group`|Необязательный. Если `dependencyType` атрибута задано значение `install`, определяет именованную группу сборок, устанавливаются только по требованию. Подробнее см. в разделе [Пошаговое руководство. Загрузка сборок по требованию с помощью API развертывания ClickOnce с использованием конструктора](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Если значение `framework` и `dependencyType` атрибута задано значение `prerequisite`, необходимая сборка в составе .NET Framework. Глобальный кэш (GAC) не проверяется для этой сборки, при установке на [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] и более поздних версиях.|  
|`codeBase`|Требуется, если `dependencyType` атрибута задано значение `install`. Путь к зависимой сборки. Может быть абсолютный путь или путь относительно кода манифеста базовым. Этот путь должен быть допустимым URI в порядке для манифеста сборки был допустимым.|  
|`size`|Требуется, если `dependencyType` атрибута задано значение `install`. Размер зависимая сборка, в байтах.|  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 Обязательно. Этот элемент является дочерним по отношению к элементу `dependentAssembly` и содержит следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`name`|Обязательно. Определяет имя приложения.|  
|`version`|Обязательно. Указывает номер версии приложения в следующем формате: `major.minor.build.revision`|  
|`publicKeyToken`|Необязательный. Указывает символ 16 шестнадцатеричную строку, которая представляет собой последние 8 байтов `SHA-1` хэш-значение открытого ключа, которым подписана приложения или сборки. Открытый ключ, используемый для подписи каталога должен быть не менее 2048 бит.|  
|`processorArchitecture`|Необязательный. Задает процессор. Допустимые значения: `x86` для 32-разрядной версии Windows и `I64` для 64-разрядной версии Windows.|  
|`language`|Необязательный. Идентифицирует две части кодов языка, например EN-US, сборки.|  
  
### <a name="hash"></a>hash  
 `hash` Элемент является необязательным и дочерним для `assemblyIdentity` элемента. `hash` Элемент не имеет атрибутов.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] использует алгоритмической хэш всех файлов в приложении в качестве проверки безопасности, чтобы убедиться, что ни один из файлов был изменен после развертывания. Если `hash` элемент не был включен, эта проверка не выполняется. Поэтому, пропустив `hash` элемента не рекомендуется.  
  
### <a name="dsigtransforms"></a>DSIG:TRANSFORMS  
 `dsig:Transforms` Элемент является обязательным дочерним элементом `hash` элемента. `dsig:Transforms` Элемент не имеет атрибутов.  
  
### <a name="dsigtransform"></a>DSIG:Transform  
 `dsig:Transform` Элемент является обязательным дочерним элементом `dsig:Transforms` элемента. `dsig:Transform` Элемент имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Algorithm`|Алгоритм, используемый для вычисления хэш-кода для этого файла. В настоящее время единственным значением, используемые [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] — `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
### <a name="dsigdigestmethod"></a>DSIG:DigestMethod  
 `dsig:DigestMethod` Элемент является обязательным дочерним элементом `hash` элемента. `dsig:DigestMethod` Элемент имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Algorithm`|Алгоритм, используемый для вычисления хэш-кода для этого файла. В настоящее время единственным значением, используемые [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] — `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
### <a name="dsigdigestvalue"></a>DSIG:DigestValue  
 `dsig:DigestValue` Элемент является обязательным дочерним элементом `hash` элемента. `dsig:DigestValue` Элемент не имеет атрибутов. Его текстовое значение представляет собой вычисленный хэш для указанного файла.  
  
## <a name="remarks"></a>Примечания  
 Все сборки, используемые вашим приложением должны иметь соответствующий `dependency` элемента. Зависимые сборки не включают сборки, которые должны быть предварительно установлены в глобальном кэше сборок как сборок платформы.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан `dependency` элементов в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифеста приложения. Данный пример кода является частью большего примера, приведенного для [манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md) раздела.  
  
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
  
## <a name="see-also"></a>См. также  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<зависимость > элемент](../deployment/dependency-element-clickonce-deployment.md)