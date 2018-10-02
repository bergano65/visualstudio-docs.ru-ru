---
title: 'CA1504: Проверьте имена полей, вводит в заблуждение | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 651d1897b06cd7d7d214fcfbfd25a3be13f60ed7
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591114"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: проверьте имена полей, которые могут ввести в заблуждение
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1504: Проверьте имена полей, вводит в заблуждение](https://docs.microsoft.com/visualstudio/code-quality/ca1504-review-misleading-field-names).

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Категория|Microsoft.Maintainability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Имя поля экземпляра начинается с «s_» или имя `static` (`Shared` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) поля начинается с «m_».

## <a name="rule-description"></a>Описание правила
 Имена полей, начинающиеся с «s_» связаны с статических данных несколькими пользователями. Аналогичным образом имена полей, начинающиеся с «m_» связаны с данными экземпляра (элемент). Для упрощения поддержки кода имена должны следовать тонкостях соглашения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, переименование поля, используя соответствующий префикс. Кроме того, сделать поле соответствующим суффиксом текущего, добавляя или удаляя `static` модификатор.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.



