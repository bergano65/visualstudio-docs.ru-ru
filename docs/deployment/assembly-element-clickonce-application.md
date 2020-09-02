---
title: '&lt;&gt;элемент Assembly (приложение ClickOnce) | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b629243920021adc3833f43f268f05638029dc7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900764"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;&gt;элемент Assembly (приложение ClickOnce)
Элемент верхнего уровня для манифеста приложения.

## <a name="syntax"></a>Синтаксис

```xml

      <assembly
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 `assembly`Элемент является корневым и является обязательным. Его первый содержащийся элемент должен быть `assemblyIdentity` элементом. Элементы манифеста должны находиться в одном из следующих пространств имен:

 `urn:schemas-microsoft-com:asm.v1`

 `urn:schemas-microsoft-com:asm.v2`

 `http://www.w3.org/2000/09/xmldsig#`

 Дочерние элементы сборки также должны находиться в этих пространствах имен путем наследования или добавления тегов.

 Элемент `assembly` имеет указанный ниже атрибут.

|Атрибут|Описание|
|---------------|-----------------|
|`manifestVersion`|Обязательный. `manifestVersion`Атрибуту должно быть присвоено значение `1.0` .|

## <a name="example"></a>Пример
 В следующем примере кода показан `assembly` элемент в манифесте приложения для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. Этот пример кода является частью большого примера, приведенного в [манифесте приложения ClickOnce](../deployment/clickonce-application-manifest.md).

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
```

## <a name="see-also"></a>См. также раздел
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<assembly> дерев](../deployment/assembly-element-clickonce-deployment.md)
