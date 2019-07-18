---
title: CA2228. Не поставляйте предварительные форматы ресурсов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f8a672056c8663c2e27ec730e542083aee9738f
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714976"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228. Не поставляйте предварительные форматы ресурсов

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Файл ресурсов был создан с помощью версии платформы .NET, которая в настоящее время не поддерживается.

## <a name="rule-description"></a>Описание правила

Файлы ресурсов, которые были созданы с помощью предварительных версий .NET может не работать в поддерживаемых версиях платформы .NET.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, ресурс сборки с помощью поддерживаемой версии .NET.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.
