---
title: '&lt;&gt;элемент assemblyIdentity (развертывание ClickOnce) | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155727"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;&gt;элемент assemblyIdentity (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет основную сборку [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения.  
  
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
 `assemblyIdentity`Элемент является обязательным. Он не содержит дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`name`|Обязательный. Определяет удобное для восприятия имя развертывания в информационных целях.<br /><br /> Если `name` содержит специальные символы, например одинарные или двойные кавычки, приложение может не выполнить активацию.|  
|`version`|Обязательный. Указывает номер версии сборки в следующем формате: `major.minor.build.revision` .<br /><br /> Это значение должно быть увеличено в обновленном манифесте для активации обновления приложения.|  
|`publicKeyToken`|Обязательный. Задает 16-символьную шестнадцатеричную строку, представляющую последние 8 байт хэш-значения SHA 1 открытого ключа, для которого подписан манифест развертывания. Открытый ключ, используемый для подписи, должен иметь значение 2048 бит или больше.<br /><br /> Несмотря на то что подписывание сборки рекомендуется, но необязательно, этот атрибут является обязательным. Если сборка не подписана, следует скопировать значение из самозаверяющего сборки или использовать фиктивные значения всех нулей.|  
|`processorArchitecture`|Обязательный. Указывает процессор. Допустимые значения: `msil` для всех процессоров, `x86` для 32-разрядных ОС Windows, `IA64` для 64-разрядной версии Windows и `Itanium` для процессоров Intel 64-bit Itanium.|  
|`type`|Обязательный. Для обеспечения совместимости с технологией параллельной установки Windows. Единственным допустимым значением является `win32` .|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан `assemblyIdentity` элемент в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифесте развертывания. Этот пример кода является частью большого примера, приведенного в разделе [манифеста развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) .  
  
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
  
## <a name="see-also"></a>См. также:  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity> Элемент](../deployment/assemblyidentity-element-clickonce-application.md)
