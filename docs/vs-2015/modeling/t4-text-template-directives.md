---
title: T4 Директивы текстовых шаблонов | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: douge
ms.openlocfilehash: e079b21c3a85f883351808b8defda6d0d68619f7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563640"
---
# <a name="t4-text-template-directives"></a>Директивы текстовых шаблонов T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [директивы текстовых шаблонов T4](https://docs.microsoft.com/visualstudio/modeling/t4-text-template-directives).  
  
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
  
 Кроме того, можно создавать собственные директивы. Дополнительные сведения см. в разделе [Создание пользовательских обработчиков текстовых шаблонов T4 директива](../modeling/creating-custom-t4-text-template-directive-processors.md). При использовании пакета SDK визуализации и моделирования для создания доменного языка в составе доменного языка будет создан обработчик директив.



