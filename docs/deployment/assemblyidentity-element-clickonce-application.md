---
title: '&lt;&gt;элемент assemblyIdentity (приложение ClickOnce) | Документация Майкрософт'
description: Элемент assemblyIdentity необходим в приложении ClickOnce. Он не содержит дочерних элементов и содержит атрибуты, описанные в этой статье.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 92b5c1d323634bbb242cdccb54890908d5668803
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911378"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;&gt;элемент assemblyIdentity (приложение ClickOnce)
Определяет приложение, развернутое в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывании.

## <a name="syntax"></a>Синтаксис

```xml

      <assemblyIdentity
   name
   version
   publicKeyToken
   processorArchitecture
   language
/>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 `assemblyIdentity`Элемент является обязательным. Он не содержит дочерних элементов и имеет следующие атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`Name`|Обязательный элемент. Определяет имя приложения.<br /><br /> Если `Name` содержит специальные символы, например одинарные или двойные кавычки, приложение может не выполнить активацию.|
|`Version`|Обязательный элемент. Указывает номер версии приложения в следующем формате: `major.minor.build.revision`|
|`publicKeyToken`|Необязательный элемент. Задает 16-символьную шестнадцатеричную строку, представляющую последние 8 байт `SHA-1` хэш-значения открытого ключа, для которого подписано приложение или сборка. Открытый ключ, используемый для подписи каталога, должен иметь длину 2048 бит или больше.<br /><br /> Несмотря на то что подписывание сборки рекомендуется, но необязательно, этот атрибут является обязательным. Если сборка не подписана, следует скопировать значение из самозаверяющего сборки или использовать фиктивные значения всех нулей.|
|`processorArchitecture`|Обязательный элемент. Указывает процессор. Допустимые значения: `msil` для всех процессоров, `x86` для 32-разрядных ОС Windows, `IA64` для 64-разрядной версии Windows и `Itanium` для процессоров Intel 64-bit Itanium.|
|`language`|Обязательный элемент. Определяет коды языка двух частей (например, `en-US` ) сборки. Этот элемент находится в `asmv2` пространстве имен. Если значение не указано, по умолчанию используется значение `neutral` .|

## <a name="examples"></a>Примеры

### <a name="description"></a>Описание
 В следующем примере кода показан `assemblyIdentity` элемент в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифесте приложения. Этот пример кода является частью большого примера, приведенного в [манифесте приложения ClickOnce](../deployment/clickonce-application-manifest.md).

### <a name="code"></a>Код

```xml
<asmv1:assemblyIdentity
  name="My Application Deployment.exe"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  type="win32" />
```

## <a name="see-also"></a>См. также
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
- [Элемент \<assemblyIdentity>](../deployment/assemblyidentity-element-clickonce-deployment.md)