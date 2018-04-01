---
title: '&lt;assemblyIdentity&gt; элемент (развертывание ClickOnce) | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 23
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 51643b8db91c9f8c2961b319d47cdfb7789f6a4d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity&gt; элемент (развертывание ClickOnce)
Определяет основной сборки [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `assemblyIdentity` Элемент является обязательным. Он не содержит дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`name`|Обязательно. Определяет понятное имя развертывания в ознакомительных целях.<br /><br /> Если `name` содержит специальные символы, такие как одинарные или двойные кавычки, приложение может вызвать сбой активации.|  
|`version`|Обязательно. Указывает номер версии сборки, в следующем формате: `major.minor.build.revision`.<br /><br /> Обновленный манифест для запуска обновления приложения необходимо увеличить это значение.|  
|`publicKeyToken`|Обязательно. Указывает символ 16 шестнадцатеричную строку, которая представляет собой последние 8 байтов хэша SHA-1 открытого ключа, которым подписана манифест развертывания. Открытый ключ, используемый для входа должно быть 2048 бит или больше.<br /><br /> Несмотря на то, что подпись сборки, рекомендуется, но необязательно, этот атрибут является обязательным. Если сборка не подписана, следует скопировать значение из самозаверяющий сборки или используйте значение «пустой» все нули.|  
|`processorArchitecture`|Обязательно. Задает процессор. Допустимые значения: `msil` для всех процессоров `x86` для 32-разрядной версии Windows, `IA64` для 64-разрядной версии Windows, и `Itanium` для Intel 64-разрядных процессоров Itanium.|  
|`type`|Обязательно. Для обеспечения совместимости с технологией Windows side-by-side установки. Единственным допустимым значением является `win32`.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан `assemblyIdentity` элемент в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест развертывания. Данный пример кода является частью большего примера, приведенного для [манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) раздела.  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity > элемент](../deployment/assemblyidentity-element-clickonce-application.md)