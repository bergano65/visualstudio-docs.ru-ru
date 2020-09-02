---
title: '&lt;&gt;элемент публишеридентити (развертывание ClickOnce) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 486e0bc5059e041f02e8dac4836c5ff59b27f63e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157630"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;&gt;элемент публишеридентити (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Содержит сведения об издателе, подписавшем этот манифест развертывания.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `publisherIdentity`Элемент необходим для подписанных манифестов. В следующей таблице показаны атрибуты, `publisherIdentity` поддерживаемые элементом.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`name`|Обязательный. Описание удостоверения стороны, опубликовавшего приложение.|  
|`issuerKeyHash`|Обязательный. Содержит хэш SHA-1 открытого ключа издателя сертификата.|  
  
#### <a name="parameters"></a>Параметры  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
  
## <a name="exceptions"></a>Исключения  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>Требования  
  
## <a name="subhead"></a>Подзаголовок
