---
title: Правила документации
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- rules, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f4ec6a0dd154dae89145add26c60a8b1322a444
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808656"
---
# <a name="documentation-rules"></a>Правила документации

Правила документации поддерживают написание хорошо документированных библиотек посредством правильного использования [комментариев XML-документации](/dotnet/csharp/codedoc) для внешних видимых интерфейсов API.

## <a name="in-this-section"></a>Содержание раздела

| Правило | Описание |
| - | - |
| [CA1200: Избегайте использования тегов cref с префиксом](../code-quality/ca1200.md) | Атрибут [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) в ТЕГЕ документации XML означает "ссылка на код". Он указывает, что текст внутри тега представляет собой элемент кода, например тип, метод или свойство. Старайтесь не использовать `cref` теги с префиксами, так как это не позволяет компилятору проверять ссылки. Это также предотвращает Поиск и обновление этих ссылок на символы во время рефакторинга в интегрированной среде разработки (IDE) Visual Studio. |

## <a name="see-also"></a>См. также раздел

- [Правила анализа кода](../code-quality/code-analysis-for-managed-code-warnings.md)
