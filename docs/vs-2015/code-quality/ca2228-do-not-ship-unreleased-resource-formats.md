---
title: 'CA2228: не поставлять невыпущенные форматы ресурсов | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9297ea0bb24eed54d0134a5f3c0fce87e6757adb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662888"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: не следует поставлять невыпущенные форматы ресурсов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Файл ресурсов был создан с использованием версии [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], которая в настоящее время не поддерживается.

## <a name="rule-description"></a>Описание правила
 Файлы ресурсов, созданные с помощью предварительных версий [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], могут не использоваться поддерживаемыми версиями .NET Framework.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, создайте ресурс с помощью поддерживаемой версии [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]k.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.
