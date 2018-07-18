---
title: 'CA2228: не следует поставлять невыпущенные форматы ресурсов'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f444779fc5db725c090f96ec51a86d8427a14d17
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919185"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: не следует поставлять невыпущенные форматы ресурсов
|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Файл ресурсов был создан с помощью версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , в настоящее время не поддерживается.

## <a name="rule-description"></a>Описание правила
 Файлы ресурсов, созданные с помощью предварительных версий [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] может не работать в поддерживаемых версиях платформы .NET Framework.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, постройте ресурс с помощью поддерживаемой версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]k.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.