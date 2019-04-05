---
title: CA2228. Не следует поставлять невыпущенные форматы ресурсов | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2e49953a95da10653cd29132e003fa36de5b8d4c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993063"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228. Не поставляйте предварительные форматы ресурсов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Файл ресурсов был создан с помощью версии [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , сейчас не поддерживается.

## <a name="rule-description"></a>Описание правила
 Файлы ресурсов, которые были созданы с помощью предварительных версий [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] может не работать в поддерживаемых версиях платформы .NET Framework.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, создания ресурса, используя поддерживаемую версию [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]k.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.
