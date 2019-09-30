---
title: Предупреждения о документации
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation warnings
- managed code analysis warnings, documentation warnings
- warnings, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00b42dc20b228e30a9b2632a0525a1ec8a9ddbb1
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079202"
---
# <a name="documentation-warnings"></a>Предупреждения о документации

Предупреждения документации поддерживают написание хорошо документированных библиотек посредством правильного использования [комментариев XML-документации](https://docs.microsoft.com/dotnet/csharp/codedoc) для внешних видимых интерфейсов API.

## <a name="in-this-section"></a>Содержание раздела

| Правило | Описание |
| - | - |
| [CA1200: Избегайте использования тегов cref с префиксом](../code-quality/ca1200.md) | Атрибут [cref](https://docs.microsoft.com/dotnet/csharp/programming-guide/xmldoc/cref-attribute) в ТЕГЕ документации XML означает "ссылка на код". Он указывает, что текст внутри тега представляет собой элемент кода, например тип, метод или свойство. Старайтесь не `cref` использовать теги с префиксами, так как это не позволяет компилятору проверять ссылки. Это также предотвращает Поиск и обновление этих ссылок на символы во время рефакторинга в интегрированной среде разработки (IDE) Visual Studio. |

## <a name="see-also"></a>См. также

- [Предупреждения анализа кода](../code-quality/code-analysis-for-managed-code-warnings.md)
