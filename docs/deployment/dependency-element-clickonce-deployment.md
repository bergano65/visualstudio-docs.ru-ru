---
title: '&lt;зависимость&gt; элемент (развертывание ClickOnce) | Документация Майкрософт'
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
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84e26a2d7dae70e0029817d4e6bb6e70dd53bce4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928954"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;зависимость&gt; элемент (развертывание ClickOnce)
Определяет версию приложения для установки и расположение манифеста приложения.

## <a name="syntax"></a>Синтаксис

```xml

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

 `dependency` Элемент обычно выражает зависимости для основного приложения для сборок, содержащихся в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. Если приложение Main.exe использует сборку DotNetAssembly.dll, этой сборки должны быть перечислены в разделе зависимостей. Зависимость, тем не менее, также можно выразить другие типы зависимостей, такие как зависимость от определенной версии среды CLR, от сборки в глобальный кэш сборок (GAC) или COM-объекта. Так как он является технологией развертывания нет-touch, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] не может инициировать загрузку и установку этих типов зависимостей, но она может помешать выполнению приложения Если один или несколько указанных зависимостей не существует.

## <a name="dependentassembly"></a>dependentAssembly
 Обязательный. Этот элемент содержит `assemblyIdentity` элемент. В следующей таблице показаны атрибуты `dependentAssembly` поддерживает.

| Атрибут | Описание |
|------------------| - |
| `preRequisite` | Необязательный параметр. Указывает, что эта сборка должна уже существовать в глобальном кэше СБОРОК. Допустимые значения: `true` и `false`. Если `true`и указанная сборка не существует в глобальном кэше СБОРОК, приложение не запускается. |
| `visible` | Необязательный параметр. Определяет идентификатор приложения верхнего уровня, включая все зависимости. Используется внутренне [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] для управления хранилищем приложения и активации. |
| `dependencyType` | Обязательный. Связь между этой зависимости и приложением. Допустимые значения:<br /><br /> -   `install`. Компонент представляет отдельной установкой из текущего приложения.<br />-   `preRequisite`. Компонент, необходимый для текущего приложения. |
| `codebase` | Необязательный параметр. Полный путь к манифесту приложения. |
| `size` | Необязательный параметр. Размер манифеста приложения, в байтах. |

## <a name="assemblyidentity"></a>assemblyIdentity
 Обязательный. Этот элемент является дочерним по отношению к элементу `dependentAssembly` . Содержание `assemblyIdentity` должен быть таким же, как описано в разделе [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест приложения. В следующей таблице показаны атрибуты `assemblyIdentity` элемент.

|Атрибут|Описание|
|---------------|-----------------|
|`Name`|Обязательный. Определяет имя приложения.|
|`Version`|Обязательный. Указывает номер версии приложения, в следующем формате: `major.minor.build.revision`|
|`publicKeyToken`|Обязательный. Задает 16-знаковая шестнадцатеричную строку, которая представляет последние 8 байтов хэша SHA-1 открытого ключа, которым подписаны приложение или сборка. Открытый ключ, используемый для входа должно быть 2048 бит или более поздней версии.|
|`processorArchitecture`|Обязательный. Указание микропроцессора. Допустимые значения: `x86` для 32-разрядной Windows и `IA64` для 64-разрядной Windows.|
|`Language`|Необязательный параметр. Определяет две части кодов языка сборки. Например EN-US, предназначенную для английского языка (США). Значение по умолчанию — `neutral`. Этот элемент имеет `asmv2` пространства имен.|
|`type`|Необязательный параметр. Для обеспечения обратной совместимости с Windows side-by-side установить технологии. Единственное допустимое значение — `win32`.|

## <a name="hash"></a>hash
 `hash` Элемент является необязательного дочернего элемента `file` элемент. У элемента `hash` нет атрибутов.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] использует алгоритма хэш всех файлов в приложении как средство проверки безопасности, чтобы убедиться, что ни один из файлов был изменен после развертывания. Если `hash` элемент не включен, эта проверка не выполняется. Таким образом, пропуск `hash` элемента не рекомендуется.

## <a name="dsigtransforms"></a>DSIG:TRANSFORMS
 `dsig:Transforms` Элемент является обязательным дочерним элементом `hash` элемент. У элемента `dsig:Transforms` нет атрибутов.

## <a name="dsigtransform"></a>DSIG:Transform
 `dsig:Transform` Элемент является обязательным дочерним элементом `dsig:Transforms` элемент. В следующей таблице показаны атрибуты `dsig:Transform` элемент.

| Атрибут | Описание |
|-------------| - |
| `Algorithm` | Алгоритм, используемый для вычисления хэш-кода для этого файла. В настоящее время единственное значение, используемое [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] является `urn:schemas-microsoft-com:HashTransforms.Identity`. |

## <a name="dsigdigestmethod"></a>DSIG:DigestMethod
 `dsig:DigestMethod` Элемент является обязательным дочерним элементом `hash` элемент. В следующей таблице показаны атрибуты `dsig:DigestMethod` элемент.

| Атрибут | Описание |
|-------------| - |
| `Algorithm` | Алгоритм, используемый для вычисления хэш-кода для этого файла. В настоящее время единственное значение, используемое [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] является `http://www.w3.org/2000/09/xmldsig#sha1`. |

## <a name="dsigdigestvalue"></a>DSIG:DigestValue
 `dsig:DigestValue` Элемент является обязательным дочерним элементом `hash` элемент. У элемента `dsig:DigestValue` нет атрибутов. Его текстовое значение является хэшем для указанного файла.

## <a name="remarks"></a>Примечания
 Манифесты развертывания обычно имеют один `assemblyIdentity` элемент, который определяет имя и версию манифеста приложения.

## <a name="example"></a>Пример
 В следующем коде показано в примере `dependency` элемент [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест развертывания.

```xml
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
 В следующем примере кода определяет зависимость от сборки уже установлены в глобальном кэше СБОРОК.

```xml
<dependency>
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />
  </dependentAssembly>
</dependency>
```

## <a name="example"></a>Пример
 В следующем примере кода указана зависимость от определенной версии среды CLR.

```xml
<dependency>
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />
  </dependentAssembly>
</dependency>
```

## <a name="example"></a>Пример
 В следующем примере кода задает зависимость операционной системы.

```xml
<dependency>
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">
      <osVersionInfo>
         <os majorVersion="4" minorVersion="10" />
      </osVersionInfo>
   </dependentOS>
</dependency>
```

## <a name="see-also"></a>См. также
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<зависимость > элемент](../deployment/dependency-element-clickonce-application.md)