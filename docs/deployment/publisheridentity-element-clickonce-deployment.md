---
title: '&lt;&gt;элемент публишеридентити (развертывание ClickOnce) | Документация Майкрософт'
description: Элемент Публишеридентити содержит сведения о издателе, который подписал манифест развертывания. Элемент необходим для подписанных манифестов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1eb4b67bfdca13c63480f3dde82004d87cd4a12a
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350690"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;&gt;элемент публишеридентити (развертывание ClickOnce)
Содержит сведения об издателе, подписавшем этот манифест развертывания.

## <a name="syntax"></a>Синтаксис

```xml
<publisherIdentity
   name
   issuerKeyHash
/>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 `publisherIdentity`Элемент необходим для подписанных манифестов. В следующей таблице показаны атрибуты, `publisherIdentity` поддерживаемые элементом.

|Атрибут|Описание|
|---------------|-----------------|
|`name`|Обязательный элемент. Описание удостоверения стороны, опубликовавшего приложение.|
|`issuerKeyHash`|Обязательный элемент. Содержит хэш SHA-1 открытого ключа издателя сертификата.|

#### <a name="parameters"></a>Параметры

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение

## <a name="exceptions"></a>Исключения

## <a name="remarks"></a>Remarks

## <a name="requirements"></a>Требования

## <a name="subhead"></a>Подзаголовок