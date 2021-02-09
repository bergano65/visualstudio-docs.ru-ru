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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65f225f8e3dd3f6d2b3afb2d2a5284d172d4fab1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891297"
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