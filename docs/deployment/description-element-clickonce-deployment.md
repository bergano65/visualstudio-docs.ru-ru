---
title: '&lt;Описание&gt; элемент (развертывание ClickOnce) | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 4701bc77350d080ef9ad9c1eb56b80c344b0ff0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Описание&gt; элемент (развертывание ClickOnce)
Определение сведений о приложении, используемый для создания оболочки присутствия и **Установка и удаление программ** элемента панели управления.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Элемент `description` обязателен и находится в пространстве имен `urn:schemas-microsoft-com:asm.v1`. Он не содержит дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`publisher`|Обязательно. Идентифицирует имя компании, используемое для размещения значка в Windows **запустить** меню и **Установка и удаление программ** элемента панели управления, если развертывание настроено для установки.|  
|`product`|Обязательно. Определяет полное название продукта. Используется в качестве названия значка, установленного в Windows **запустить** меню.|  
|`suiteName`|Необязательный. Указывает вложенную `publisher` папки в Windows **запустить** меню.|  
|`supportUrl`|Необязательный. Указывает URL-адрес поддержки, который отображается в **Установка и удаление программ** элемента панели управления. Ярлык этот URL-адрес также создается для поддержки приложения в Windows **запустить** меню, если развертывание настроено для установки.|  
  
## <a name="remarks"></a>Примечания  
 Элемент описания является обязательным во всех конфигурациях развертывания.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан `description` элемент в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест развертывания. Данный пример кода является частью большего примера, приведенного для [манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) раздела.  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)