---
title: '&lt;сборка&gt; элемент (развертывание ClickOnce) | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 96978ec8329ddf31b2cc641bf02d2b38a9e98f4a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560245"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;сборка&gt; элемент (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ &lt;сборки&gt; элемент (развертывание ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/assembly-element-clickonce-deployment).  
  
Элемент верхнего уровня для манифеста развертывания.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `assembly` Элемент является корневым элементом и является обязательным. Его первый содержащийся элемент должен быть `assemblyIdentity` элемент. Манифеста элементы должны быть в следующих пространствах имен: `urn:schemas-microsoft-com:asm.v1`, `urn:schemas-microsoft-com:asm.v2`, и `http://www.w3.org/2000/09/xmldsig#`. Дочерние элементы сборки также необходимо включить в эти пространства имен путем наследования или маркировки.  
  
 `assembly` Элемент имеет следующий атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`manifestVersion`|Обязательно. Этот атрибут должно быть присвоено `1.0`.|  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано `assembly` элемент в манифест развертывания для приложения, развернутого с помощью [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Данный пример кода является частью большего примера для [манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) раздела.  
  
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



