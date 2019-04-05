---
title: '&lt;зависимость&gt; элемент (приложение ClickOnce) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e79fadcab1a4f00c084d675c3267b5886772fe2c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980491"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;зависимость&gt; элемент (приложение ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет зависимость платформы или сборки, необходимые для приложения.  
  
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
 Необязательный параметр. Содержит `osVersionInfo` элемент. `dependentOS` И `dependentAssembly` элементы являются взаимоисключающими: одно из них должен существовать для `dependency` , но не оба.  
  
 `dependentOS` поддерживает следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`supportUrl`|Необязательный параметр. Указывает URL-адрес поддержки для зависимой платформы. Этот URL-адрес отображается для пользователя при обнаружении платформе.|  
|`description`|Необязательный параметр. Описание операционной системы, описываемых в удобное для восприятия форме `dependentOS` элемент.|  
  
### <a name="osversioninfo"></a>osVersionInfo  
 Обязательный. Этот элемент является дочерним по отношению к элементу `dependentOS` и содержит элемент `os` . Этот элемент не содержит атрибуты.  
  
### <a name="os"></a>ОС  
 Обязательный. Этот элемент является дочерним по отношению к элементу `osVersionInfo` . Этот элемент содержит следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`majorVersion`|Обязательный. Указывает основной номер версии операционной системы.|  
|`minorVersion`|Обязательный. Указывает дополнительный номер версии операционной системы.|  
|`buildNumber`|Обязательный. Указывает номер сборки операционной системы.|  
|`servicePackMajor`|Обязательный. Указывает основной номер пакета обновления операционной системы.|  
|`servicePackMinor`|Необязательный параметр. Указывает дополнительный номер пакета обновления операционной системы.|  
|`productType`|Необязательный параметр. Определяет значение типа продукта. Допустимые значения: `server`, `workstation` и `domainController`. Например, для Windows 2000 Professional, это значение атрибута равно `workstation`.|  
|`suiteType`|Необязательный параметр. Определяет набор продуктов, доступных в системе, или тип конфигурации системы. Допустимые значения: `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted` и `terminal`. Например, для Windows 2000 Professional, это значение атрибута равно `professional`.|  
  
### <a name="dependentassembly"></a>dependentAssembly  
 Необязательный параметр. Содержит `assemblyIdentity` элемент. `dependentOS` И `dependentAssembly` элементы являются взаимоисключающими: одно из них должен существовать для `dependency` , но не оба.  
  
 `dependentAssembly` имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`dependencyType`|Обязательный. Указывает тип зависимости. Допустимые значения: `preprequisite` и `install`. `install` Сборка устанавливается как часть [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения. Объект `prerequisite` сборки должен присутствовать в глобальный кэш сборок (GAC) перед [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложение разрешено устанавливать.|  
|`allowDelayedBinding`|Обязательный. Указывает, можно ли загрузить программными средствами во время выполнения сборки.|  
|`group`|Необязательный параметр. Если `dependencyType` атрибут имеет значение `install`, назначает это именованная группа сборки устанавливаются, только по запросу. Дополнительные сведения см. в разделе [Пошаговое руководство: загрузка сборок по требованию с помощью API развертывания ClickOnce с использованием конструктора](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Если значение `framework` и `dependencyType` атрибут имеет значение `prerequisite`, определяет сборку как часть платформы .NET Framework. Глобальный кэш (GAC) не проверяется для этой сборки, при установке на [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] и более поздних версий.|  
|`codeBase`|Требуется, если `dependencyType` атрибут имеет значение `install`. Путь к зависимой сборки. Может быть абсолютный путь или путь относительно кода манифеста базовым. Этот путь должен быть допустимым URI в порядке для манифеста сборки был допустимым.|  
|`size`|Требуется, если `dependencyType` атрибут имеет значение `install`. Размер зависимой сборки, в байтах.|  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 Обязательный. Этот элемент является дочерним по отношению к элементу `dependentAssembly` и содержит следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`name`|Обязательный. Определяет имя приложения.|  
|`version`|Обязательный. Указывает номер версии приложения в следующем формате: `major.minor.build.revision`|  
|`publicKeyToken`|Необязательный параметр. Указывает, 16-знаковая шестнадцатеричную строку, которая представляет собой последние 8 байт `SHA-1` хэш-значение открытого ключа, которым подписаны приложение или сборка. Открытый ключ, используемый для подписи каталога должен быть не менее 2048 бит.|  
|`processorArchitecture`|Необязательный параметр. Указывает процессор. Допустимые значения: `x86` для 32-разрядной Windows и `I64` для 64-разрядной Windows.|  
|`language`|Необязательный параметр. Определяет две части кодов языка, например EN-US, сборки.|  
  
### <a name="hash"></a>hash  
 `hash` Элемент является необязательного дочернего элемента `assemblyIdentity` элемент. У элемента `hash` нет атрибутов.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] использует алгоритма хэш всех файлов в приложении в качестве проверки безопасности, чтобы убедиться, что ни один из файлов был изменен после развертывания. Если `hash` элемент не включен, эта проверка не выполняется. Таким образом, пропуск `hash` элемента не рекомендуется.  
  
### <a name="dsigtransforms"></a>DSIG:TRANSFORMS  
 `dsig:Transforms` Элемент является обязательным дочерним элементом `hash` элемент. У элемента `dsig:Transforms` нет атрибутов.  
  
### <a name="dsigtransform"></a>DSIG:Transform  
 `dsig:Transform` Элемент является обязательным дочерним элементом `dsig:Transforms` элемент. Элемент `dsig:Transform` имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Algorithm`|Алгоритм, используемый для вычисления хэш-кода для этого файла. В настоящее время единственное значение, используемое [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] является `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
### <a name="dsigdigestmethod"></a>DSIG:DigestMethod  
 `dsig:DigestMethod` Элемент является обязательным дочерним элементом `hash` элемент. Элемент `dsig:DigestMethod` имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Algorithm`|Алгоритм, используемый для вычисления хэш-кода для этого файла. В настоящее время единственное значение, используемое [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] является `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
### <a name="dsigdigestvalue"></a>DSIG:DigestValue  
 `dsig:DigestValue` Элемент является обязательным дочерним элементом `hash` элемент. У элемента `dsig:DigestValue` нет атрибутов. Его текстовое значение является хэшем для указанного файла.  
  
## <a name="remarks"></a>Примечания  
 Все сборки, используемый в приложении должна быть определена соответствующая `dependency` элемент. Зависимые сборки не включают сборки, которые должны быть предварительно установлены в глобальном кэше сборок как сборки платформы.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано `dependency` элементов в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест приложения. Данный пример кода является частью большего примера для [манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md) раздела.  
  
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
 [Элемент \<dependency>](../deployment/dependency-element-clickonce-deployment.md)
