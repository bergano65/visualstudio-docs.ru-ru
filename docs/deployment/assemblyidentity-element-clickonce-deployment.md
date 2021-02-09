---
title: '&lt;&gt;элемент assemblyIdentity (развертывание ClickOnce) | Документация Майкрософт'
description: Элемент assemblyIdentity необходим в развертывании ClickOnce. Он не содержит дочерних элементов и содержит атрибуты, описанные в этой статье.
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
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bc689c80d033c6b92178f020c0d3273f6ec86ca7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911346"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;&gt;элемент assemblyIdentity (развертывание ClickOnce)
Определяет основную сборку [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения.

## <a name="syntax"></a>Синтаксис

```xml

      <assemblyIdentity  
   name 
   version
   publicKeyToken
   processorArchitecture
    type
/>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 `assemblyIdentity`Элемент является обязательным. Он не содержит дочерних элементов и имеет следующие атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`name`|Обязательный элемент. Определяет удобное для восприятия имя развертывания в информационных целях.<br /><br /> Если `name` содержит специальные символы, например одинарные или двойные кавычки, приложение может не выполнить активацию.|
|`version`|Обязательный элемент. Указывает номер версии сборки в следующем формате: `major.minor.build.revision` .<br /><br /> Это значение должно быть увеличено в обновленном манифесте для активации обновления приложения.|
|`publicKeyToken`|Обязательный элемент. Задает 16-символьную шестнадцатеричную строку, представляющую последние 8 байт хэш-значения SHA 1 открытого ключа, для которого подписан манифест развертывания. Открытый ключ, используемый для подписи, должен иметь значение 2048 бит или больше.<br /><br /> Несмотря на то что подписывание сборки рекомендуется, но необязательно, этот атрибут является обязательным. Если сборка не подписана, следует скопировать значение из самозаверяющего сборки или использовать фиктивные значения всех нулей.|
|`processorArchitecture`|Обязательный элемент. Указывает процессор. Допустимые значения: `msil` для всех процессоров, `x86` для 32-разрядных ОС Windows, `IA64` для 64-разрядной версии Windows и `Itanium` для процессоров Intel 64-bit Itanium.|
|`type`|Обязательный элемент. Для обеспечения совместимости с технологией параллельной установки Windows. Единственным допустимым значением является `win32` .|

## <a name="remarks"></a>Remarks

## <a name="example"></a>Пример
 В следующем примере кода показан `assemblyIdentity` элемент в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифесте развертывания. Этот пример кода является частью большого примера, приведенного в разделе [манифеста развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) .

```xml
<!-- Identify the deployment. -->
<assemblyIdentity
  name="My Application Deployment.app"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>См. также раздел
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Элемент \<assemblyIdentity>](../deployment/assemblyidentity-element-clickonce-application.md)