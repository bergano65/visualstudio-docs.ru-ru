---
title: '&lt;&gt;элемент Assembly (развертывание ClickOnce) | Документация Майкрософт'
description: Элемент Assembly является корневым и требуется в развертывании ClickOnce. Его первый содержащийся элемент должен быть элементом assemblyIdentity.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b7838e0a212bbc1e743783255106bb44561fbe62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837766"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;&gt;элемент Assembly (развертывание ClickOnce)
Элемент верхнего уровня для манифеста развертывания.

## <a name="syntax"></a>Синтаксис

```xml

      <assembly  
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 `assembly`Элемент является корневым и является обязательным. Его первый содержащийся элемент должен быть `assemblyIdentity` элементом. Элементы манифеста должны находиться в следующих пространствах имен: `urn:schemas-microsoft-com:asm.v1` , `urn:schemas-microsoft-com:asm.v2` и `http://www.w3.org/2000/09/xmldsig#` . Дочерние элементы сборки также должны находиться в этих пространствах имен путем наследования или добавления тегов.

 Элемент `assembly` имеет указанный ниже атрибут.

|Атрибут|Описание|
|---------------|-----------------|
|`manifestVersion`|Обязательный элемент. Для этого атрибута необходимо задать значение `1.0` .|

## <a name="example"></a>Пример
 В следующем примере кода показан `assembly` элемент в манифесте развертывания для приложения, развернутого с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Этот пример кода является частью большого примера, приведенного в разделе [манифеста развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) .

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
```

## <a name="see-also"></a>См. также раздел
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Элемент \<assembly>](../deployment/assembly-element-clickonce-application.md)