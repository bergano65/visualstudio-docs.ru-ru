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
ms.openlocfilehash: b3c6298c2186b6a73b4a7ef441b5f4c42c90ff6a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231063"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228. Не поставляйте предварительные форматы ресурсов

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Файл ресурсов был создан с использованием версии .NET, которая в настоящее время не поддерживается.

## <a name="rule-description"></a>Описание правила

Файлы ресурсов, созданные с помощью предварительных версий .NET, могут не использоваться поддерживаемыми версиями .NET.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, создайте ресурс с помощью поддерживаемой версии .NET.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует.
