---
title: "Элемент &lt;dependency&gt; (развертывание ClickOnce) | Microsoft Docs"
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
  - "<dependency> - элемент [манифест развертывания ClickOnce]"
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 27
---
# Элемент &lt;dependency&gt; (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет версию устанавливаемого приложения и расположение манифеста приложения.  
  
## Синтаксис  
  
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
  
## Элементы и атрибуты  
 Элемент `dependency` является обязательным.  В нем нет атрибутов.  Манифест развертывания может иметь несколько элементов `dependency`.  
  
 Элемент `dependency` обычно выражает зависимости для главного приложения от сборок, содержащихся в приложении [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Если приложение Main.exe включает сборку DotNetAssembly.dll, то эта сборка должна быть указана в разделе зависимостей.  Однако зависимость может также выражать другие типы зависимостей, например зависимости от определенной версии среды CLR, от сборки в глобальном кэше сборок \(GAC\) или от объекта COM.  Поскольку эта технология развертывания "без вмешательства", [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] не может инициировать загрузку и установку этих типов зависимостей, но предотвращает запуск приложения в случае, когда одна или несколько указанных зависимостей не существуют.  
  
## dependentAssembly  
 Обязательный.  Этот элемент содержит элемент `assemblyIdentity`.  В следующей таблице перечислены атрибуты, поддерживаемые элементом `dependentAssembly`.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`preRequisite`|Необязательный.  Указание того, что данная сборка уже должна присутствовать в GAC.  Допустимые значения: `true` и `false`.  Если присвоено значение `true` и указанная сбор отсутствует в GAC, запуск приложения невозможен.|  
|`visible`|Необязательный.  Определение удостоверения приложения верхнего уровня, включая его зависимости.  Предназначен для внутреннего использования в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] для управления хранением и активацией приложений.|  
|`dependencyType`|Обязательный.  Связь между зависимостью и приложением.  Допустимые значения:<br /><br /> -   `install`.  Компонент обозначает установку отдельно от текущего приложения.<br />-   `preRequisite`.  Компонент необходим текущему приложению.|  
|`codebase`|Необязательный.  Полный путь к манифесту приложения.|  
|`size`|Необязательный.  Размер манифеста приложения в байтах.|  
  
## assemblyIdentity  
 Обязательный.  Этот элемент является дочерним для элемента `dependentAssembly`.  Содержимое `assemblyIdentity` должно совпадать с описанием в манифесте приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  В следующей таблице перечислены атрибуты элемента `assemblyIdentity`.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Name`|Обязательный.  Идентифицирует имя приложения.|  
|`Version`|Обязательный.  Указание номера версии приложения в следующем формате: `старший разряд.младший разряд.построение.редакция`|  
|`publicKeyToken`|Обязательный.  Задание 16\-символьной шестнадцатеричной строки, которая представляет последние 8 байтов хэша SHA\-1 открытого ключа, которым приложение или сборка подписывается.  Открытый ключ доступа, используемый для подписи, должен иметь длину не менее 2048 бит.|  
|`processorArchitecture`|Обязательный.  Указание микропроцессора.  Действующие значения `x86` для 32\-битового Windows и `IA64` для 64\-битового Windows.|  
|`Language`|Необязательный.  Определение двух частей кодов языка сборки.  Например, EN\-US для "Английский \(США\)".  По умолчанию используется значение `neutral`.  Этот элемент находится в пространстве имен `asmv2`.|  
|`type`|Необязательный.  Для обратной совместимости с технологией параллельной установки Windows.  Единственным допустимым значением является `win32`.|  
  
## hash  
 Элемент `hash` является необязательным дочерним элементом элемента `file`.  У элемента `hash` отсутствуют атрибуты.  
  
 Чтобы гарантировать, что ни один из файлов не был изменен после развертывания, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] использует алгоритмический хэш всех файлов в приложении.  Если элемент `hash` не включен, такая проверка выполняться не будет. Поэтому не рекомендуется пропускать элемент `hash`.  
  
## dsig:Transforms  
 Элемент `dsig:Transforms` является обязательным дочерним элементом элемента `hash`.  У элемента `dsig:Transforms` отсутствуют атрибуты.  
  
## dsig:Transform  
 Элемент `dsig:Transform` является обязательным дочерним элементом элемента `dsig:Transforms`.  В следующей таблице отображены атрибуты элемента `dsig:Transform`.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Algorithm`|Алгоритм, используемый для вычисления дайджеста для этого файла.  В настоящее время значением, используемым [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], может быть только `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## dsig:DigestMethod  
 Элемент `dsig:DigestMethod` является обязательным дочерним элементом элемента `hash`.  В следующей таблице отображены атрибуты элемента `dsig:DigestMethod`.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Algorithm`|Алгоритм, используемый для вычисления дайджеста для этого файла.  В настоящее время [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] может использовать только значение `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## dsig:DigestValue  
 Элемент `dsig:DigestValue` является обязательным дочерним элементом элемента `hash`.  У элемента `dsig:DigestValue` отсутствуют атрибуты.  Его текстовое значение – это вычисленный хэш для указанного файла.  
  
## Заметки  
 Обычно манифест развертывания имеет один элемент `assemblyIdentity`, идентифицирующий имя и версию манифеста приложения.  
  
## Пример  
 В следующем примере кода показан элемент `dependency` в манифесте развертывания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
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
  
## Пример  
 В следующем примере кода указывается зависимость от сборки, уже установленной в GAC.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## Пример  
 В следующем примере кода указывается зависимость от определенной версии среды CLR.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## Пример  
 В следующем примере кода указывается зависимость от операционной системы.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Элемент \<dependency\>](../deployment/dependency-element-clickonce-application.md)