---
title: "&lt;зависимость&gt; элемент (развертывание ClickOnce) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 8716da20c989a1a8d1e36d9e071e9802a06219bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;зависимость&gt; элемент (развертывание ClickOnce)
Определяет версию устанавливаемого приложения и расположение манифеста приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
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
  
   </dependentAssembly>   
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `dependency` Элемент является обязательным. Он не имеет атрибутов. Манифест развертывания может иметь несколько `dependency` элементов.  
  
 `dependency` Элемент обычно выражает зависимости для главного приложения от сборок, содержащихся в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. Если приложение Main.exe использует сборку DotNetAssembly.dll, этой сборки должны быть перечислены в разделе зависимостей. Зависимость, однако также можно выразить другие типы зависимостей, например зависимости от определенной версии среды CLR, от сборки в глобальный кэш сборок (GAC) или COM-объекта. Так как он является технологией развертывания без вмешательства, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] не может инициировать загрузку и установку этих типов зависимостей, но может помешать выполнению приложения Если один или несколько указанных зависимостей не существует.  
  
## <a name="dependentassembly"></a>dependentAssembly  
 Обязательно. Этот элемент содержит `assemblyIdentity` элемента. В следующей таблице показаны атрибуты `dependentAssembly` поддерживает.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`preRequisite`|Необязательный. Указывает, что эта сборка должна уже существовать в глобальном кэше СБОРОК. Допустимые значения: `true` и `false`. Если `true`и указанная сборка не существует в глобальном кэше СБОРОК, приложение не запускается.|  
|`visible`|Необязательный. Определяет идентификатор приложения верхнего уровня, включая его зависимости. Используется внутренним образом [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] для управления хранилищем приложений и активации.|  
|`dependencyType`|Обязательно. Связь между этой зависимости и приложением. Допустимые значения:<br /><br /> -   `install`. Компонент представляет установку отдельно от текущего приложения.<br />-   `preRequisite`. Компонент, необходимый для текущего приложения.|  
|`codebase`|Необязательный. Полный путь к манифесту приложения.|  
|`size`|Необязательный. Размер манифеста приложения, в байтах.|  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Обязательно. Этот элемент является дочерним по отношению к элементу `dependentAssembly`. Содержимое `assemblyIdentity` должен быть таким же, как описано в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифеста приложения. В следующей таблице показаны атрибуты `assemblyIdentity` элемента.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Name`|Обязательно. Определяет имя приложения.|  
|`Version`|Обязательно. Указывает номер версии приложения, в следующем формате:`major.minor.build.revision`|  
|`publicKeyToken`|Обязательно. Указывает символ 16 шестнадцатеричную строку, которая представляет собой последние 8 байтов хэша SHA-1 открытого ключа, которым подписана приложения или сборки. Открытый ключ, используемый для входа должно быть 2048 бит или больше.|  
|`processorArchitecture`|Обязательно. Указание микропроцессора. Допустимые значения: `x86` для 32-разрядной версии Windows и `IA64` для 64-разрядной версии Windows.|  
|`Language`|Необязательный. Идентифицирует две части кодов языка сборки. Например EN-US, предназначенную для английского языка (США). Значение по умолчанию — `neutral`. Этот элемент имеет `asmv2` пространства имен.|  
|`type`|Необязательный. Для обеспечения обратной совместимости с Windows side-by-side устанавливает технологии. Единственным допустимым значением является `win32`.|  
  
## <a name="hash"></a>hash  
 `hash` Элемент является необязательным и дочерним для `file` элемента. `hash` Элемент не имеет атрибутов.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]использует алгоритмической хэш всех файлов в приложении как проверка безопасности, чтобы убедиться, что ни один из файлов был изменен после развертывания. Если `hash` элемент не был включен, эта проверка не выполняется. Поэтому, пропустив `hash` элемента не рекомендуется.  
  
## <a name="dsigtransforms"></a>DSIG:TRANSFORMS  
 `dsig:Transforms` Элемент является обязательным дочерним элементом `hash` элемента. `dsig:Transforms` Элемент не имеет атрибутов.  
  
## <a name="dsigtransform"></a>DSIG:Transform  
 `dsig:Transform` Элемент является обязательным дочерним элементом `dsig:Transforms` элемента. В следующей таблице показаны атрибуты `dsig:Transform` элемента.  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|`Algorithm`|Алгоритм, используемый для вычисления хэш-кода для этого файла. В настоящее время единственным значением, используемые [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] — `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## <a name="dsigdigestmethod"></a>DSIG:DigestMethod  
 `dsig:DigestMethod` Элемент является обязательным дочерним элементом `hash` элемента. В следующей таблице показаны атрибуты `dsig:DigestMethod` элемента.  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|`Algorithm`|Алгоритм, используемый для вычисления хэш-кода для этого файла. В настоящее время единственным значением, используемые [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] — `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## <a name="dsigdigestvalue"></a>DSIG:DigestValue  
 `dsig:DigestValue` Элемент является обязательным дочерним элементом `hash` элемента. `dsig:DigestValue` Элемент не имеет атрибутов. Его текстовое значение представляет собой вычисленный хэш для указанного файла.  
  
## <a name="remarks"></a>Примечания  
 Манифесты развертывания обычно имеют один `assemblyIdentity` элемент, который определяет имя и версию манифеста приложения.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан `dependency` элемент в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест развертывания.  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Пример  
 В следующем примере кода указана зависимость от сборки уже установлены в глобальном кэше СБОРОК.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Пример  
 В следующем примере кода указана зависимость от определенной версии среды CLR.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Пример  
 В следующем примере кода указана зависимость от операционной системы.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## <a name="see-also"></a>См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<зависимость > элемент](../deployment/dependency-element-clickonce-application.md)