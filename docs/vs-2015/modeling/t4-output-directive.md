---
title: Директива вывода T4 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 149370bfee1b142876dff881625d08083afadea4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652317"
---
# <a name="t4-output-directive"></a>Директива Output T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В текстовых шаблонах [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] директива `output` используется для определения расширения файла и кодировки преобразованного файла.

 Например, если [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] проект содержит файл шаблона с именем **MyTemplate.TT** , содержащий следующую директиву:

 `<#@output extension=".cs"#>`

 затем [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] создаст файл с именем **MyTemplate.CS**

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
 Задает кодировку для использования при создании выходного файла. Например:

 `<#@ output encoding="utf-8"#>`

 Значение по умолчанию — кодировка, используемая файлом текстового шаблона.

 Допустимые значения: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (Система по умолчанию)

 Как правило, можно использовать строку WebName или число CodePage любых кодировок, возвращаемых <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.
