---
title: T4 Директивы текстовых шаблонов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
ms.assetid: 6898ee02-ebb2-4635-a4e9-350774c13cf2
caps.latest.revision: 83
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6f5c4c474ad737add8580381e7fda5fb0b0c1afc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044841"
---
# <a name="t4-text-template-directives"></a>Директивы текстовых шаблонов T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
 Кроме того, можно создавать собственные директивы. Дополнительные сведения см. в разделе [Создание пользовательских обработчиков текстовых шаблонов T4 директива](../modeling/creating-custom-t4-text-template-directive-processors.md). При использовании пакета SDK визуализации и моделирования для создания доменного языка (SDL) в составе доменного языка будет создан обработчик директив.
