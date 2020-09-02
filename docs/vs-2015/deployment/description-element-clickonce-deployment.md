---
title: '&lt;&gt;элемент Description (развертывание ClickOnce) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cadf4a0b525e5603247748edd63516dc26d8a0b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187749"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;&gt;элемент Description (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет сведения о приложении, используемом для создания оболочки, а также элемент « **Установка и удаление программ** » в панели управления.  
  
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
 Элемент `description` является обязательным и находится в пространстве имен `urn:schemas-microsoft-com:asm.v1` . Он не содержит дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`publisher`|Обязательный. Определяет название компании, используемое для размещения значков в меню " **Пуск** " Windows, а также элемент " **Установка и удаление программ** " на панели управления, если развертывание настроено для установки.|  
|`product`|Обязательный. Определяет полное название продукта. Используется в качестве заголовка для значка, установленного в меню " **Пуск** " Windows.|  
|`suiteName`|Необязательный элемент. Определяет вложенную папку в `publisher` папке в меню " **Пуск** " Windows.|  
|`supportUrl`|Необязательный элемент. Указывает URL-адрес поддержки, который отображается в элементе " **Установка и удаление программ** " панели управления. Ярлык для этого URL-адреса также создается для поддержки приложений в меню " **Пуск** " Windows, когда развертывание настроено для установки.|  
  
## <a name="remarks"></a>Remarks  
 Элемент description является обязательным во всех конфигурациях развертывания.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан `description` элемент в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифесте развертывания. Этот пример кода является частью большого примера, приведенного в разделе [манифеста развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) .  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>См. также:  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)
