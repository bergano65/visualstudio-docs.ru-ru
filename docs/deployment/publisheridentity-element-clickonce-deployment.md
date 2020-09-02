---
title: '&lt;&gt;элемент публишеридентити (развертывание ClickOnce) | Документация Майкрософт'
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
ms.openlocfilehash: 995b002784c1e76ceed36e51edb1ae893448f448
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62927543"
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
|`name`|Обязательный. Описание удостоверения стороны, опубликовавшего приложение.|
|`issuerKeyHash`|Обязательный. Содержит хэш SHA-1 открытого ключа издателя сертификата.|

#### <a name="parameters"></a>Параметры

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение

## <a name="exceptions"></a>Исключения

## <a name="remarks"></a>Remarks

## <a name="requirements"></a>Требования

## <a name="subhead"></a>Подзаголовок