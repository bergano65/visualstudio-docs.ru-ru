---
title: '&lt;элемент&gt; Dependency (приложение ClickOnce) | Документация Майкрософт'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3aa949aa2f8e718ab0209c54a0ea2160c042a4eb
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252486"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;элемент&gt; Dependency (приложение ClickOnce)
Определяет зависимость платформы или сборки, необходимую для приложения.

## <a name="syntax"></a>Синтаксис

```xml

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
 `dependency` Элемент является обязательным. `dependency` В одном манифесте приложения может быть несколько экземпляров.

 `dependency` Элемент не имеет атрибутов и содержит следующие дочерние элементы.

### <a name="dependentos"></a>депендентос
 Необязательный параметр. `osVersionInfo` Содержит элемент. Элементы `dependentOS` `dependency` и `dependentAssembly` являются взаимоисключающими: один или другой должен существовать для элемента, но не для обоих.

 `dependentOS`поддерживает следующие атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`supportUrl`|Необязательный параметр. Указывает URL-адрес поддержки для зависимой платформы. Этот URL-адрес отображается пользователю, если требуется найти требуемую платформу.|
|`description`|Необязательный параметр. Описывает, в удобочитаемой форме, операционной системе, описываемой `dependentOS` элементом.|

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
|`servicePackMinor`|Необязательный параметр. Указывает дополнительный номер пакета обновления операционной системы.|
|`productType`|Необязательный параметр. Определяет значение типа продукта. Допустимые значения: `server`, `workstation` и `domainController`. Например, для Windows 2000 Professional это значение атрибута — `workstation`.|
|`suiteType`|Необязательный параметр. Определяет набор продуктов, доступный в системе, или тип конфигурации системы. Допустимые значения: `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted` и `terminal`. Например, для Windows 2000 Professional это значение атрибута — `professional`.|

### <a name="dependentassembly"></a>dependentAssembly
 Необязательный параметр. `assemblyIdentity` Содержит элемент. Элементы `dependentOS` `dependency` и `dependentAssembly` являются взаимоисключающими: один или другой должен существовать для элемента, но не для обоих.

 `dependentAssembly`имеет следующие атрибуты.

| Атрибут | Описание |
|-----------------------| - |
| `dependencyType` | Обязательный. Указывает тип зависимости. Допустимые значения: `preprequisite` и `install`. Сборка устанавливается как часть [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. `install` Чтобы приложение можно было установить, Сборкадолжнаприсутствоватьвглобальномкэшесборок(GAC).`prerequisite` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] |
| `allowDelayedBinding` | Обязательный. Указывает, может ли сборка загружаться программно во время выполнения. |
| `group` | Необязательный параметр. Если атрибут имеет `install`значение, то обозначает именованную группу сборок, которые устанавливаются только по запросу. `dependencyType` Дополнительные сведения см. в разделе [Пошаговое руководство: загрузка сборок по требованию с помощью API развертывания ClickOnce с использованием конструктора](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Если задано `framework` значение `dependencyType` и для атрибута задано `prerequisite`значение, то сборка обозначается как часть .NET Framework. Глобальный кэш Assembly (GAC) не проверяется для этой сборки при установке на .NET Framework 4 и более поздних версиях. |
| `codeBase` | Требуется, `dependencyType` если атрибуту `install`присвоено значение. Путь к зависимой сборке. Может быть абсолютным путем или путем относительно базы кода манифеста. Этот путь должен быть допустимым URI, чтобы манифест сборки был допустимым. |
| `size` | Требуется, `dependencyType` если атрибуту `install`присвоено значение. Размер зависимой сборки в байтах. |

### <a name="assemblyidentity"></a>assemblyIdentity
 Обязательный. Этот элемент является дочерним по отношению к элементу `dependentAssembly` и содержит следующие атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`name`|Обязательный. Определяет имя приложения.|
|`version`|Обязательный. Указывает номер версии приложения в следующем формате:`major.minor.build.revision`|
|`publicKeyToken`|Необязательный параметр. Задает 16-символьную шестнадцатеричную строку, представляющую последние 8 байт `SHA-1` хэш-значения открытого ключа, для которого подписано приложение или сборка. Открытый ключ, используемый для подписи каталога, должен быть 2048 или более.|
|`processorArchitecture`|Необязательный параметр. Указывает процессор. Допустимые значения: `x86` для 32-разрядных Windows `I64` и для 64-разрядной версии Windows.|
|`language`|Необязательный параметр. Определяет две части кода языка (например, EN-US) сборки.|

### <a name="hash"></a>hash
 Элемент является необязательным дочерним `assemblyIdentity` элементом элемента. `hash` У элемента `hash` нет атрибутов.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]использует алгоритмный хэш всех файлов приложения в качестве проверки безопасности, чтобы гарантировать, что ни один из файлов не был изменен после развертывания. `hash` Если элемент не включен, эта проверка не будет выполнена. Поэтому не рекомендуется опускать `hash` элемент.

### <a name="dsigtransforms"></a>дсиг: преобразования
 Элемент является обязательным дочерним `hash` элементом элемента. `dsig:Transforms` У элемента `dsig:Transforms` нет атрибутов.

### <a name="dsigtransform"></a>дсиг: преобразование
 Элемент является обязательным дочерним `dsig:Transforms` элементом элемента. `dsig:Transform` Элемент `dsig:Transform` имеет перечисленные ниже атрибуты.

| Атрибут | Описание |
|-------------| - |
| `Algorithm` | Алгоритм, используемый для вычисления дайджеста для этого файла. В настоящее время единственным значением, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] используемым, является `urn:schemas-microsoft-com:HashTransforms.Identity`. |

### <a name="dsigdigestmethod"></a>дсиг: Дижестмесод
 Элемент является обязательным дочерним `hash` элементом элемента. `dsig:DigestMethod` Элемент `dsig:DigestMethod` имеет перечисленные ниже атрибуты.

| Атрибут | Описание |
|-------------| - |
| `Algorithm` | Алгоритм, используемый для вычисления дайджеста для этого файла. В настоящее время единственным значением, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] используемым, является `http://www.w3.org/2000/09/xmldsig#sha1`. |

### <a name="dsigdigestvalue"></a>дсиг: Дижествалуе
 Элемент является обязательным дочерним `hash` элементом элемента. `dsig:DigestValue` У элемента `dsig:DigestValue` нет атрибутов. Его текстовое значение — это вычисленный хэш для указанного файла.

## <a name="remarks"></a>Примечания
 Все сборки, используемые приложением, должны иметь соответствующий `dependency` элемент. Зависимые сборки не включают сборки, которые должны быть предварительно установлены в глобальный кэш сборок в качестве сборок платформы.

## <a name="example"></a>Пример
 В следующем примере кода показаны `dependency` элементы [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] в манифесте приложения. Этот пример кода является частью большого примера, приведенного в разделе [манифеста приложения ClickOnce](../deployment/clickonce-application-manifest.md) .

```xml
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
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<Элемент > зависимости](../deployment/dependency-element-clickonce-deployment.md)