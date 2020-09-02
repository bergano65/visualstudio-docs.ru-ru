---
title: '&lt;&gt;элемент dependency (развертывание ClickOnce) | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928954"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;&gt;элемент dependency (развертывание ClickOnce)
Определяет версию устанавливаемого приложения и расположение манифеста приложения.

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
 `dependency`Элемент является обязательным. У него нет атрибутов. Манифест развертывания может содержать несколько `dependency` элементов.

 `dependency`Элемент обычно выражает зависимости для основного приложения в сборках, содержащихся в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложении. Если приложение Main.exe использует сборку с именем DotNetAssembly.dll, то эта сборка должна быть указана в разделе зависимости. Однако зависимость также может выразить другие типы зависимостей, например зависимости от конкретной версии среды CLR, для сборки в глобальном кэше сборок (GAC) или для COM-объекта. Так как это технология развертывания без участия пользователя, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] не может инициировать скачивание и установку этих типов зависимостей, но она предотвращает запуск приложения, если одна или несколько указанных зависимостей не существуют.

## <a name="dependentassembly"></a>dependentAssembly
 Обязательный. Этот элемент содержит `assemblyIdentity` элемент. В следующей таблице показаны атрибуты, `dependentAssembly` Поддерживаемые.

| Атрибут | Описание |
|------------------| - |
| `preRequisite` | Необязательный элемент. Указывает, что эта сборка уже должна существовать в глобальном кэше сборок. Допустимые значения: `true` и `false`. Если `true` , а указанная сборка не существует в глобальном кэше сборок, приложение не сможет запуститься. |
| `visible` | Необязательный элемент. Определяет удостоверение приложения верхнего уровня, включая его зависимости. Используется для внутренних целей [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] для управления хранением и активацией приложений. |
| `dependencyType` | Обязательный. Отношение между этой зависимостью и приложением. Допустимые значения:<br /><br /> -   `install`. Компонент представляет собой отдельную установку из текущего приложения.<br />-   `preRequisite`. Компонент является обязательным для текущего приложения. |
| `codebase` | Необязательный элемент. Полный путь к манифесту приложения. |
| `size` | Необязательный элемент. Размер манифеста приложения в байтах. |

## <a name="assemblyidentity"></a>assemblyIdentity
 Обязательный. Этот элемент является дочерним по отношению к элементу `dependentAssembly` . Содержимое `assemblyIdentity` должно быть таким же, как описано в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифесте приложения. В следующей таблице показаны атрибуты `assemblyIdentity` элемента.

|Атрибут|Описание|
|---------------|-----------------|
|`Name`|Обязательный. Определяет имя приложения.|
|`Version`|Обязательный. Указывает номер версии приложения в следующем формате: `major.minor.build.revision`|
|`publicKeyToken`|Обязательный. Задает 16-символьную шестнадцатеричную строку, представляющую последние 8 байт хэша SHA-1 открытого ключа, для которого подписано приложение или сборка. Открытый ключ, используемый для подписи, должен иметь длину 2048 бит или более.|
|`processorArchitecture`|Обязательный. Задает микропроцессор. Допустимые значения: `x86` для 32-разрядных Windows и `IA64` для 64-разрядной версии Windows.|
|`Language`|Необязательный элемент. Определяет два кода языка сборки. Например, EN-US, который обозначает английский язык (США). Значение по умолчанию — `neutral`. Этот элемент находится в `asmv2` пространстве имен.|
|`type`|Необязательный элемент. Для обратной совместимости с технологией параллельной установки Windows. Единственным допустимым значением является `win32` .|

## <a name="hash"></a>hash
 `hash`Элемент является необязательным дочерним элементом `file` элемента. У элемента `hash` нет атрибутов.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] использует алгоритмный хэш всех файлов приложения в качестве проверки безопасности, чтобы гарантировать, что ни один из файлов не был изменен после развертывания. Если `hash` элемент не включен, эта проверка не будет выполнена. Поэтому `hash` не рекомендуется опускать элемент.

## <a name="dsigtransforms"></a>дсиг: преобразования
 `dsig:Transforms`Элемент является обязательным дочерним элементом `hash` элемента. У элемента `dsig:Transforms` нет атрибутов.

## <a name="dsigtransform"></a>дсиг: преобразование
 `dsig:Transform`Элемент является обязательным дочерним элементом `dsig:Transforms` элемента. В следующей таблице показаны атрибуты `dsig:Transform` элемента.

| Атрибут | Описание |
|-------------| - |
| `Algorithm` | Алгоритм, используемый для вычисления дайджеста для этого файла. В настоящее время единственным значением, используемым, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] является `urn:schemas-microsoft-com:HashTransforms.Identity` . |

## <a name="dsigdigestmethod"></a>дсиг: Дижестмесод
 `dsig:DigestMethod`Элемент является обязательным дочерним элементом `hash` элемента. В следующей таблице показаны атрибуты `dsig:DigestMethod` элемента.

| Атрибут | Описание |
|-------------| - |
| `Algorithm` | Алгоритм, используемый для вычисления дайджеста для этого файла. В настоящее время единственным значением, используемым, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] является `http://www.w3.org/2000/09/xmldsig#sha1` . |

## <a name="dsigdigestvalue"></a>дсиг: Дижествалуе
 `dsig:DigestValue`Элемент является обязательным дочерним элементом `hash` элемента. У элемента `dsig:DigestValue` нет атрибутов. Его текстовое значение — это вычисленный хэш для указанного файла.

## <a name="remarks"></a>Remarks
 Манифесты развертывания обычно содержат единственный `assemblyIdentity` элемент, определяющий имя и версию манифеста приложения.

## <a name="example"></a>Пример
 В следующем примере кода показан `dependency` элемент в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифесте развертывания.

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
 В следующем примере кода задается зависимость от сборки, уже установленной в GAC.

```xml
<dependency>
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />
  </dependentAssembly>
</dependency>
```

## <a name="example"></a>Пример
 В следующем примере кода задается зависимость от определенной версии среды CLR.

```xml
<dependency>
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />
  </dependentAssembly>
</dependency>
```

## <a name="example"></a>Пример
 В следующем примере кода задается зависимость операционной системы.

```xml
<dependency>
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">
      <osVersionInfo>
         <os majorVersion="4" minorVersion="10" />
      </osVersionInfo>
   </dependentOS>
</dependency>
```

## <a name="see-also"></a>См. также раздел
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<dependency> дерев](../deployment/dependency-element-clickonce-application.md)