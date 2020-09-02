---
title: '&lt;&gt;элемент dependency (приложение ClickOnce) | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199885"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;&gt;элемент dependency (приложение ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет зависимость платформы или сборки, необходимую для приложения.  
  
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
 `dependency`Элемент является обязательным. `dependency`В одном манифесте приложения может быть несколько экземпляров.  
  
 `dependency`Элемент не имеет атрибутов и содержит следующие дочерние элементы.  
  
### <a name="dependentos"></a>депендентос  
 Необязательный элемент. Содержит `osVersionInfo` элемент. `dependentOS`Элементы и `dependentAssembly` являются взаимоисключающими: один или другой должен существовать для `dependency` элемента, но не для обоих.  
  
 `dependentOS` поддерживает следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`supportUrl`|Необязательный элемент. Указывает URL-адрес поддержки для зависимой платформы. Этот URL-адрес отображается пользователю, если требуется найти требуемую платформу.|  
|`description`|Необязательный элемент. Описывает, в удобочитаемой форме, операционной системе, описываемой `dependentOS` элементом.|  
  
### <a name="osversioninfo"></a>осверсионинфо  
 Обязательный. Этот элемент является дочерним по отношению к элементу `dependentOS` и содержит элемент `os` . Этот элемент не содержит атрибуты.  
  
### <a name="os"></a>ОС  
 Обязательный. Этот элемент является дочерним по отношению к элементу `osVersionInfo` . Этот элемент содержит следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`majorVersion`|Обязательный. Указывает основной номер версии операционной системы.|  
|`minorVersion`|Обязательный. Указывает дополнительный номер версии операционной системы.|  
|`buildNumber`|Обязательный. Указывает номер сборки ОС.|  
|`servicePackMajor`|Обязательный. Указывает номер основного номера пакета обновления операционной системы.|  
|`servicePackMinor`|Необязательный элемент. Указывает дополнительный номер пакета обновления операционной системы.|  
|`productType`|Необязательный элемент. Определяет значение типа продукта. Допустимые значения: `server`, `workstation` и `domainController`. Например, для Windows 2000 Professional это значение атрибута — `workstation` .|  
|`suiteType`|Необязательный элемент. Определяет набор продуктов, доступный в системе, или тип конфигурации системы. Допустимые значения: `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted` и `terminal`. Например, для Windows 2000 Professional это значение атрибута — `professional` .|  
  
### <a name="dependentassembly"></a>dependentAssembly  
 Необязательный элемент. Содержит `assemblyIdentity` элемент. `dependentOS`Элементы и `dependentAssembly` являются взаимоисключающими: один или другой должен существовать для `dependency` элемента, но не для обоих.  
  
 `dependentAssembly` имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`dependencyType`|Обязательный. Указывает тип зависимости. Допустимые значения: `preprequisite` и `install`. `install`Сборка устанавливается как часть [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения. `prerequisite`Чтобы приложение можно было установить, сборка должна присутствовать в глобальном кэше сборок (GAC) [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .|  
|`allowDelayedBinding`|Обязательный. Указывает, может ли сборка загружаться программно во время выполнения.|  
|`group`|Необязательный элемент. Если `dependencyType` атрибут имеет значение, то `install` обозначает именованную группу сборок, которые устанавливаются только по запросу. Дополнительные сведения см. в разделе [Пошаговое руководство: скачивание сборок по требованию с помощью API развертывания ClickOnce с использованием конструктора](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Если задано значение `framework` и для `dependencyType` атрибута задано значение `prerequisite` , то сборка обозначается как часть .NET Framework. Глобальный кэш Assembly (GAC) не проверяется для этой сборки при установке в [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] и более поздних версиях.|  
|`codeBase`|Требуется, если `dependencyType` атрибуту присвоено значение `install` . Путь к зависимой сборке. Может быть абсолютным путем или путем относительно базы кода манифеста. Этот путь должен быть допустимым URI, чтобы манифест сборки был допустимым.|  
|`size`|Требуется, если `dependencyType` атрибуту присвоено значение `install` . Размер зависимой сборки в байтах.|  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 Обязательный. Этот элемент является дочерним по отношению к элементу `dependentAssembly` и содержит следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`name`|Обязательный. Определяет имя приложения.|  
|`version`|Обязательный. Указывает номер версии приложения в следующем формате: `major.minor.build.revision`|  
|`publicKeyToken`|Необязательный элемент. Задает 16-символьную шестнадцатеричную строку, представляющую последние 8 байт `SHA-1` хэш-значения открытого ключа, для которого подписано приложение или сборка. Открытый ключ, используемый для подписи каталога, должен быть 2048 или более.|  
|`processorArchitecture`|Необязательный элемент. Указывает процессор. Допустимые значения: `x86` для 32-разрядных Windows и `I64` для 64-разрядной версии Windows.|  
|`language`|Необязательный элемент. Определяет две части кода языка (например, EN-US) сборки.|  
  
### <a name="hash"></a>hash  
 `hash`Элемент является необязательным дочерним элементом `assemblyIdentity` элемента. У элемента `hash` нет атрибутов.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] использует алгоритмный хэш всех файлов приложения в качестве проверки безопасности, чтобы гарантировать, что ни один из файлов не был изменен после развертывания. Если `hash` элемент не включен, эта проверка не будет выполнена. Поэтому `hash` не рекомендуется опускать элемент.  
  
### <a name="dsigtransforms"></a>дсиг: преобразования  
 `dsig:Transforms`Элемент является обязательным дочерним элементом `hash` элемента. У элемента `dsig:Transforms` нет атрибутов.  
  
### <a name="dsigtransform"></a>дсиг: преобразование  
 `dsig:Transform`Элемент является обязательным дочерним элементом `dsig:Transforms` элемента. Элемент `dsig:Transform` имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Algorithm`|Алгоритм, используемый для вычисления дайджеста для этого файла. В настоящее время единственным значением, используемым, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] является `urn:schemas-microsoft-com:HashTransforms.Identity` .|  
  
### <a name="dsigdigestmethod"></a>дсиг: Дижестмесод  
 `dsig:DigestMethod`Элемент является обязательным дочерним элементом `hash` элемента. Элемент `dsig:DigestMethod` имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Algorithm`|Алгоритм, используемый для вычисления дайджеста для этого файла. В настоящее время единственным значением, используемым, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] является `http://www.w3.org/2000/09/xmldsig#sha1` .|  
  
### <a name="dsigdigestvalue"></a>дсиг: Дижествалуе  
 `dsig:DigestValue`Элемент является обязательным дочерним элементом `hash` элемента. У элемента `dsig:DigestValue` нет атрибутов. Его текстовое значение — это вычисленный хэш для указанного файла.  
  
## <a name="remarks"></a>Remarks  
 Все сборки, используемые приложением, должны иметь соответствующий `dependency` элемент. Зависимые сборки не включают сборки, которые должны быть предварительно установлены в глобальный кэш сборок в качестве сборок платформы.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показаны `dependency` элементы в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифесте приложения. Этот пример кода является частью большого примера, приведенного в разделе [манифеста приложения ClickOnce](../deployment/clickonce-application-manifest.md) .  
  
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
  
## <a name="see-also"></a>См. также:  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<dependency> Элемент](../deployment/dependency-element-clickonce-deployment.md)
