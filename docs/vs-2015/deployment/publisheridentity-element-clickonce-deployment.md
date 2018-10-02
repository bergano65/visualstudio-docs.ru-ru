---
title: '&lt;publisherIdentity&gt; элемент (развертывание ClickOnce) | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 4c11e8ed9a3e0b4341708fc849462fbc476dc395
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568244"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt; элемент (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ &lt;publisherIdentity&gt; элемент (развертывание ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/publisheridentity-element-clickonce-deployment).  
  
Содержит сведения об издателе, подписавшем этот манифест развертывания.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `publisherIdentity` Элемент является обязательным для манифестов с подписью. В следующей таблице показаны атрибуты, `publisherIdentity` поддерживает элемент.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`name`|Обязательно. Описывает удостоверение стороны, публикации этого приложения.|  
|`issuerKeyHash`|Обязательно. Содержит хэш SHA-1 открытого ключа издателя сертификата.|  
  
#### <a name="parameters"></a>Параметры  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
  
## <a name="exceptions"></a>Исключения  
  
## <a name="remarks"></a>Примечания  
  
## <a name="requirements"></a>Требования  
  
## <a name="subhead"></a>Подзаголовок



