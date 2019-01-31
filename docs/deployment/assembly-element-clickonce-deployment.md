---
title: '&lt;сборка&gt; элемент (развертывание ClickOnce) | Документация Майкрософт'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e6192c7705555e817ed82d452d703f0affd9609
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932705"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;сборка&gt; элемент (развертывание ClickOnce)
Элемент верхнего уровня для манифеста развертывания.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `assembly` Элемент является корневым элементом и является обязательным. Его первый содержащийся элемент должен быть `assemblyIdentity` элемент. Манифеста элементы должны быть в следующих пространствах имен: `urn:schemas-microsoft-com:asm.v1`, `urn:schemas-microsoft-com:asm.v2`, и `http://www.w3.org/2000/09/xmldsig#`. Дочерние элементы сборки также необходимо включить в эти пространства имен путем наследования или маркировки.  
  
 Элемент `assembly` имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`manifestVersion`|Обязательный. Этот атрибут должно быть присвоено `1.0`.|  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано `assembly` элемент в манифест развертывания для приложения, развернутого с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Данный пример кода является частью большего примера для [манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) раздела.  
  
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
  
## <a name="see-also"></a>См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<сборка > элемент](../deployment/assembly-element-clickonce-application.md)