---
title: '&lt;сборка&gt; элемент (приложение ClickOnce) | Документы Microsoft'
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
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1c72dd684092784c88b1ef6dd76d410ac9ff84d5
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704227"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;сборка&gt; элемент (приложение ClickOnce)
Элемент верхнего уровня для манифеста приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `assembly` Элемент является корневым элементом и является обязательным. Должен быть первый элемент автономной `assemblyIdentity` элемента. Элементы манифеста должны быть в одном из следующих пространств имен:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 Дочерние элементы сборки также необходимо включить в этих пространствах имен путем наследования или добавление тегов.  
  
 `assembly` Элемент имеет указанный ниже атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`manifestVersion`|Обязательно. `manifestVersion` Атрибуту должно быть присвоено `1.0`.|  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан `assembly` элемента в манифесте приложения для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. Данный пример кода является частью большего примера, приведенного в [манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md).  
  
```  
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
  
## <a name="see-also"></a>См. также  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<сборка > элемент](../deployment/assembly-element-clickonce-deployment.md)
