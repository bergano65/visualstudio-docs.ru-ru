---
title: Директивы текстовых шаблонов T4
description: Узнайте о директивах тестового шаблона T4 и о том, как они предоставляют инструкции для обработчика преобразования текстовых шаблонов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ddad0010413ebe8e0a53096bb4d90b52050d26a
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363605"
---
# <a name="t4-text-template-directives"></a>Директивы текстовых шаблонов T4

Директивы представляют собой инструкции для процессора преобразования текстового шаблона.

Синтаксис директив таков:

```
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>
```

Все значения атрибутов должны заключаться в двойные кавычки. Если значение само содержит двойные кавычки, их нужно предварять знаком \.

Как правило, директивы — это первый элемент файла шаблона или включенного файла. Их не следует помещать внутри блока кода `<#...#>` или после блока функции класса `<#+...#>`.

[Директива Template T4](../modeling/t4-template-directive.md)

```
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>
```

[Директива Parameter T4](../modeling/t4-parameter-directive.md)

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

[Директива Output T4](../modeling/t4-output-directive.md)

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

[Директива Assembly T4](../modeling/t4-assembly-directive.md)

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

[Директива Import T4](../modeling/t4-import-directive.md)

```
<#@ import namespace="namespace" #>
```

[Директива Include T4](../modeling/t4-include-directive.md)

```
<#@ include file="filePath" #>
```

[Директива T4 CleanUpBehavior](../modeling/t4-cleanupbehavior-directive.md)

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Кроме того, можно создавать собственные директивы. Дополнительные сведения см. в разделе [Создание пользовательских обработчиков директив текстовых шаблонов T4](../modeling/creating-custom-t4-text-template-directive-processors.md). При использовании пакета SDK визуализации и моделирования для создания доменного языка (SDL) в составе доменного языка будет создан обработчик директив.
