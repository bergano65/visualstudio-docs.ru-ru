---
title: Директива Output T4
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1da8ec010e878ff80a9f46748993705b87193d99
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606218"
---
# <a name="t4-output-directive"></a>Директива Output T4

В текстовых шаблонах Visual Studio директива `output` используется для определения расширения имени файла и кодировки преобразованного файла.

 Например, если проект Visual Studio содержит файл шаблона с именем **MyTemplate.TT** , содержащий следующую директиву:

 `<#@output extension=".cs"#>`

 Затем Visual Studio создаст файл с именем **MyTemplate.CS**

 Директива `output` не требуется в текстовых шаблонах времени выполнения (предварительно обработанных). Вместо этого приложение получает созданную строку, вызывая `TextTransform()`. Дополнительные сведения см. [в разделе Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Применение директивы output

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 В каждом текстовом шаблоне должна быть только одна директива `output`.

## <a name="extension-attribute"></a>атрибут расширения
 Указывает расширение файла созданного файла текстового вывода.

 Значение по умолчанию — **. cs.**

 Примеры: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Допустимые значения: любое допустимое расширение имени файла.

## <a name="encoding-attribute"></a>атрибут Encoding
 Задает кодировку для использования при создании выходного файла. Пример:

 `<#@ output encoding="utf-8"#>`

 Значение по умолчанию — кодировка, используемая файлом текстового шаблона.

 Допустимые значения: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (системное значение по умолчанию)

 Как правило, можно использовать строку WebName или число CodePage любых кодировок, возвращаемых <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.