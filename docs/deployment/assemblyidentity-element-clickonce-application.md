---
title: "&lt;assemblyIdentity&gt; элемент (приложение ClickOnce) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: "20"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: b731522897512300459a32f8e01c4d54277eaa5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity&gt; элемент (приложение ClickOnce)
Идентифицирует приложение, развернутое в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `assemblyIdentity` Элемент является обязательным. Он не содержит дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Name`|Обязательно. Определяет имя приложения.<br /><br /> Если `Name` содержит специальные символы, такие как одинарные или двойные кавычки, приложение может вызвать сбой активации.|  
|`Version`|Обязательно. Указывает номер версии приложения в следующем формате:`major.minor.build.revision`|  
|`publicKeyToken`|Необязательный. Указывает символ 16 шестнадцатеричную строку, которая представляет собой последние 8 байтов `SHA-1` хэш-значение открытого ключа, которым подписана приложения или сборки. Открытый ключ, используемый для подписи каталога должна быть 2048 бит или больше.<br /><br /> Несмотря на то, что подпись сборки, рекомендуется, но необязательно, этот атрибут является обязательным. Если сборка не подписана, следует скопировать значение из самозаверяющий сборки или используйте значение «пустой» все нули.|  
|`processorArchitecture`|Обязательно. Задает процессор. Допустимые значения: `msil` для всех процессоров `x86` для 32-разрядной версии Windows, `IA64` для 64-разрядной версии Windows, и `Itanium` для Intel 64-разрядных процессоров Itanium.|  
|`language`|Обязательно. Идентифицирует две части кодов языка (например, `en-US`) сборки. Этот элемент имеет `asmv2` пространства имен. Если не указан, значение по умолчанию — `neutral`.|  
  
## <a name="examples"></a>Примеры  
  
### <a name="description"></a>Описание:  
 В следующем примере кода показан `assemblyIdentity` элемент в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифеста приложения. Данный пример кода является частью большего примера, приведенного в [манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md).  
  
### <a name="code"></a>Код  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## <a name="see-also"></a>См. также  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity > элемент](../deployment/assemblyidentity-element-clickonce-deployment.md)