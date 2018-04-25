---
title: '&lt;сборка&gt; элемент (развертывание ClickOnce) | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ab58cb90f9486c3a233d5173db340be3ee5f034
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;сборка&gt; элемент (развертывание ClickOnce)
Элемент верхнего уровня для манифеста развертывания.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `assembly` Элемент является корневым элементом и является обязательным. Должен быть первый элемент автономной `assemblyIdentity` элемента. Элементы манифеста должны быть в следующих пространствах имен: `urn:schemas-microsoft-com:asm.v1`, `urn:schemas-microsoft-com:asm.v2`, и `http://www.w3.org/2000/09/xmldsig#`. Дочерние элементы сборки также необходимо включить в этих пространствах имен путем наследования или добавление тегов.  
  
 `assembly` Элемент имеет указанный ниже атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`manifestVersion`|Обязательно. Этот атрибут должен быть задан `1.0`.|  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан `assembly` элемента в манифесте развертывания для приложения, развернутые с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Данный пример кода является частью большего примера, приведенного для [манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) раздела.  
  
```  
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