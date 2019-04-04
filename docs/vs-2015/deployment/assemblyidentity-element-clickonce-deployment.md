---
title: '&lt;assemblyIdentity&gt; элемент (развертывание ClickOnce) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bfc2ff97a2eb465fe7306ebe368a20e2a7fd8638
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991441"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity&gt; элемент (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет основную сборку из [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения.  
  
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
|`name`|Обязательный. Определяет понятное имя развертывания в информационных целях.<br /><br /> Если `name` содержит специальные символы, такие как одинарные или двойные кавычки, приложение может вызвать сбой активации.|  
|`version`|Обязательный. Указывает номер версии сборки, в следующем формате: `major.minor.build.revision`.<br /><br /> Обновленный манифест для активации обновления приложения необходимо увеличить это значение.|  
|`publicKeyToken`|Обязательный. Задает 16-знаковая шестнадцатеричную строку, которая представляет последние 8 байтов хэша SHA-1 открытого ключа, которым подписаны манифеста развертывания. Открытый ключ, используемый для входа должно быть 2048 бит или более поздней версии.<br /><br /> Несмотря на то, что подпись сборки, рекомендуется, но необязательно, этот атрибут является обязательным. Если сборка не подписана, следует скопировать значение из собственной подписью сборки или использовать значение «пустого» все нули.|  
|`processorArchitecture`|Обязательный. Указывает процессор. Допустимые значения: `msil` для всех процессоров `x86` для 32-разрядной Windows, `IA64` для 64-разрядной Windows, и `Itanium` для Intel 64-разрядных процессоров Itanium.|  
|`type`|Обязательный. Для обеспечения совместимости с технологией side-by-side установки Windows. Единственное допустимое значение — `win32`.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано `assemblyIdentity` элемент [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест развертывания. Данный пример кода является частью большего примера для [манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) раздела.  
  
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
 [Элемент \<assemblyIdentity>](../deployment/assemblyidentity-element-clickonce-application.md)
