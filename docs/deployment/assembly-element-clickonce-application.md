---
title: '&lt;сборка&gt; элемент (приложение ClickOnce) | Документация Майкрософт'
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 35c8193c2210d2a16a7d73164b551adb5a0f06bd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53878357"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;сборка&gt; элемент (приложение ClickOnce)
Элемент верхнего уровня для манифеста приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `assembly` Элемент является корневым элементом и является обязательным. Его первый содержащийся элемент должен быть `assemblyIdentity` элемент. Элементы манифеста должен находиться в одном из следующих пространств имен:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 Дочерние элементы сборки также необходимо включить в эти пространства имен путем наследования или маркировки.  
  
 Элемент `assembly` имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`manifestVersion`|Обязательный. `manifestVersion` Атрибута должно быть присвоено `1.0`.|  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано `assembly` элемента в манифесте приложения для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. Данный пример кода является частью большего примера, приведенного в [манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md).  
  
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
  
## <a name="see-also"></a>См. также  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<сборка > элемент](../deployment/assembly-element-clickonce-deployment.md)
