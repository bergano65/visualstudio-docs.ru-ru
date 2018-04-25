---
title: '&lt;publisherIdentity&gt; элемент (развертывание ClickOnce) | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ad10cae4ebd3aee6b65ad408ea3a3df3f82fd02
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt; элемент (развертывание ClickOnce)
Содержит сведения об издателе, подписавшем этот манифест развертывания.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `publisherIdentity` Элемент является обязательным для подписанных манифестов. В следующей таблице показаны атрибуты, `publisherIdentity` поддерживает элемент.  
  
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