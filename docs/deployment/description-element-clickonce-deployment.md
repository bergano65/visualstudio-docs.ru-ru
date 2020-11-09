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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4eb1de8f5692eedc9673f1a22cb448ac8d102ae5
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382836"
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
|`suiteName`|Необязательный параметр. Определяет вложенную папку в `publisher` папке в меню " **Пуск** " Windows.|
|`supportUrl`|Необязательный параметр. Указывает URL-адрес поддержки, который отображается в элементе " **Установка и удаление программ** " панели управления. Ярлык для этого URL-адреса также создается для поддержки приложений в меню " **Пуск** " Windows, когда развертывание настроено для установки.|

## <a name="remarks"></a>Комментарии
 Элемент description является обязательным во всех конфигурациях развертывания.

## <a name="example"></a>Пример
 В следующем примере кода показан `description` элемент в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифесте развертывания. Этот пример кода является частью большого примера, приведенного в разделе [манифеста развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) .

```xml
<description
  asmv2:publisher="My Company Name"
  asmv2:product="My Application"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>См. также
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)