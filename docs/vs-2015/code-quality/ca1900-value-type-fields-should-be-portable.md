---
title: 'CA1900: поля типа значения должны быть переносимыми | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 23b5705b7ee81e56945050fe63dd2f086894bd08
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917930"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: поля типа значения должны быть переносимыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю документацию по Visual Studio см. в разделе [CA1900: value type Field reportable](/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable).

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Категория|Microsoft. переносимость|
|Критическое изменение|Критическое — если поле может отображаться за пределами сборки.<br /><br /> Не критическое — если поле не отображается за пределами сборки.|

## <a name="cause"></a>Причина:
 Это правило проверяет, должны ли структуры, объявленные с явно заданным макетом, правильно выстроиться при маршалировании в неуправляемый код в 64-разрядных операционных системах. IA-64 не допускает несогласованный доступ к памяти, и процесс будет аварийно завершиться, если это нарушение не исправлено.

## <a name="rule-description"></a>Описание правила
 Структуры с явным макетом, содержащим несогласованные поля, вызывают сбои в 64-разрядных операционных системах.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Все поля, размер которых меньше 8 байт, должны иметь смещения, кратные их размеру, а поля размером 8 байт или больше должны иметь смещения, кратные 8. Другое решение заключается в использовании `LayoutKind.Sequential` вместо `LayoutKind.Explicit`, если это оправдано.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это предупреждение следует подавлять только в том случае, если оно возникает в ошибке.
