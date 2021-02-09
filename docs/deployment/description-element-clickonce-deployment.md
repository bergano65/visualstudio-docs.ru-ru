---
title: '&lt;&gt;элемент Description (развертывание ClickOnce) | Документация Майкрософт'
description: Элемент Description определяет сведения о приложении, используемые для создания оболочки присутствия и элемента «Установка и удаление программ» в панели управления.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8dee33fca027ce47ede8315f7956479ee2394382
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893091"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;&gt;элемент Description (развертывание ClickOnce)
Определяет сведения о приложении, используемом для создания оболочки, а также элемент « **Установка и удаление программ** » в панели управления.

## <a name="syntax"></a>Синтаксис

```xml

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
|`publisher`|Обязательный элемент. Определяет название компании, используемое для размещения значков в меню " **Пуск** " Windows, а также элемент " **Установка и удаление программ** " на панели управления, если развертывание настроено для установки.|
|`product`|Обязательный элемент. Определяет полное название продукта. Используется в качестве заголовка для значка, установленного в меню " **Пуск** " Windows.|
|`suiteName`|Необязательный элемент. Определяет вложенную папку в `publisher` папке в меню " **Пуск** " Windows.|
|`supportUrl`|Необязательный элемент. Указывает URL-адрес поддержки, который отображается в элементе " **Установка и удаление программ** " панели управления. Ярлык для этого URL-адреса также создается для поддержки приложений в меню " **Пуск** " Windows, когда развертывание настроено для установки.|

## <a name="remarks"></a>Remarks
 Элемент description является обязательным во всех конфигурациях развертывания.

## <a name="example"></a>Пример
 В следующем примере кода показан `description` элемент в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифесте развертывания. Этот пример кода является частью большого примера, приведенного в разделе [манифеста развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) .

```xml
<description
  asmv2:publisher="My Company Name"
  asmv2:product="My Application"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>См. также раздел
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)