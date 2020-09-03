---
title: Предупреждения по документации
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
ms.openlocfilehash: 4946c69bbbe4bf1c240967ebd93ef58cfa79e333
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72807109"
---
# <a name="documentation-warnings"></a>Предупреждения по документации

Предупреждения документации поддерживают написание хорошо документированных библиотек посредством правильного использования [комментариев XML-документации](/dotnet/csharp/codedoc) для внешних видимых интерфейсов API.

## <a name="in-this-section"></a>В этом разделе

| Правило | Описание |
| - | - |
| [CA1200: Избегайте использования тегов cref с префиксом](../code-quality/ca1200.md) | Атрибут [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) в ТЕГЕ документации XML означает "ссылка на код". Он указывает, что текст внутри тега представляет собой элемент кода, например тип, метод или свойство. Старайтесь не использовать `cref` теги с префиксами, так как это не позволяет компилятору проверять ссылки. Это также предотвращает Поиск и обновление этих ссылок на символы во время рефакторинга в интегрированной среде разработки (IDE) Visual Studio. |

## <a name="see-also"></a>См. также

- [Предупреждения анализа кода](../code-quality/code-analysis-for-managed-code-warnings.md)
