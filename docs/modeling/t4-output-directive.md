---
title: Директива Output T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 2a7e98608a9f5885a1f14353b4a5b7fa83c2cdb6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874340"
---
# <a name="t4-output-directive"></a>Директива Output T4

В текстовых шаблонах Visual Studio `output` директива используется для определения расширение имени файла и кодировки преобразованного файла.

 Например, если проект Visual Studio включает в себя файл шаблона с именем **MyTemplate.tt** которого содержит следующую директиву:

 `<#@output extension=".cs"#>`

 Затем Visual Studio создаст файл с именем **MyTemplate.cs**

 Директива `output` не требуется в текстовых шаблонах времени выполнения (предварительно обработанных). Вместо этого приложение получает созданную строку, вызывая `TextTransform()`. Дополнительные сведения см. в разделе [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Применение директивы output

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 В каждом текстовом шаблоне должна быть только одна директива `output`.

## <a name="extension-attribute"></a>атрибут расширения
 Указывает расширение файла созданного файла текстового вывода.

 Значение по умолчанию — **.cs**

 Примеры: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Допустимые значения: любое допустимое расширение файла.

## <a name="encoding-attribute"></a>атрибут кодировки
 Задает кодировку для использования при создании выходного файла. Например:

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